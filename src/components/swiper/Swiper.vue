<template>
    <div id="hy-swiper">
      <div class="swiper" ref="swiper">
        <slot></slot>
      </div>
      <div class="right" @click="next(1)">
        <a href="javascript:;"></a>
      </div>
      <div class="left" @click="previous(-1)">
        <a href="javascript:;"></a>
      </div>
      <slot name="indicator">
      </slot>
      <div class="indicator">
        <slot name="indicator" v-if="showIndicator && slideCount>1">
          <div v-for="(item, index) in slideCount" class="indi-item" :class="{active: index === currentIndex}" :key="index"
          @click="indClick(index)">
          </div>
        </slot>
      </div>
    </div>
</template>

<script>
	export default {
		name: "Swiper",
    props: {
      interval: {
		    type: Number,
        default: 3000
      },
      animDuration: {
		    type: Number,
        default: 300
      },
      moveRatio: {
        type: Number,
        default: 0.25
      },
      showIndicator: {  //指示器，即红点是否要显示
        type: Boolean,
        default: true
      }
    },
    data: function () {
		  return {
        slideCount: 4, // 元素个数
        totalWidth: 0, // swiper的宽度
        swiperStyle: {}, // swiper样式
        currentIndex: 0, // 当前的index
        currentImg:null,//当前的图片
        scrolling: false, // 是否正在滚动
      }
    },

    methods: {
		  /**
       * 定时器操作
       */
      startTimer: function () {
		    this.playTimer = setInterval(() => {
		      this.currentIndex++;
          if (this.currentIndex >= this.slideCount ) {
            this.currentIndex = 0;
          } else if (this.currentIndex < 0) {
            this.currentIndex = this.slideCount-1;
          }
          // console.log(this.currentIndex)
		      this.$refs.swiper.appendChild(this.cloneEls[this.currentIndex],this.currentImg)
		      this.scrollContent(- this.totalWidth);
        }, 3000)

      },
      stopTimer: function () {
        clearInterval(this.playTimer);
      },
      /**
       * 操作DOM, 在DOM前后添加Slide
       */
      handleDom: function () {
        // 1.获取要操作的元素
        let swiperEl = this.$refs.swiper
        let slidesEls = swiperEl.getElementsByClassName('slide');
        //把所有图片节点克隆下来
        this.cloneEls=[].map.call(slidesEls,item=>{
          return item.cloneNode(true)
        })
        //删除所有子节点
        for(let i = slidesEls.length - 1; i >= 0; i--) {
          slidesEls[i].parentNode.removeChild(slidesEls[i]);
        }
        // 2.保存个数
        this.slideCount = this.cloneEls.length;

        //3.保存长度和style
        this.totalWidth = swiperEl.offsetWidth;
        this.swiperStyle = swiperEl.style;
        //4.初始化currentImg
        this.currentImg=this.cloneEls[0]
        this.$refs.swiper.appendChild(this.cloneEls[0])

        this.$refs.swiper.addEventListener('transitionend',()=>{
            this.$refs.swiper.removeChild(this.currentImg)
            this.currentImg=this.cloneEls[this.currentIndex]
            this.swiperStyle.transition = '0ms'; //移动结束后要调整到原始位置
            this.setTransform(0);
            this.scrolling=false
            this.swiperStyle.left='0px' //向左翻的动画结束后调整left值
        })
      },


      /**
       * 滚动到正确的位置
       */
      scrollContent: function (currentPosition) {
        // 1.开始滚动动画
        this.swiperStyle.transition ='transform '+ this.animDuration + 'ms';
        this.setTransform(currentPosition); //这里设置translate

        // 2.判断滚动到的位置
        this.checkPosition();

      },

      /**
       * 设置滚动的位置
       */
      setTransform: function (position) {
        this.swiperStyle.transform = `translate3d(${position}px, 0, 0)`;
        this.swiperStyle['-webkit-transform'] = `translate3d(${position}px), 0, 0`;
        this.swiperStyle['-ms-transform'] = `translate3d(${position}px), 0, 0`;
      },
      /**
       * 校验正确的位置
       */
      checkPosition: function () {
        if (this.currentIndex >= this.slideCount ) {
          this.currentIndex = 0;
        } else if (this.currentIndex < 0) {
          this.currentIndex = this.slideCount-1;
        }
      },


      /**
       * 控制上一个, 下一个
       */
      previous: function (num) {
        // 1.移除定时器
        this.stopTimer();
        if(!this.scrolling){
          this.scrolling=true
          this.swiperStyle.left=`-${this.totalWidth}px` //向左翻之前先调整left值让整体左移一个宽度
          this.currentIndex = this.currentIndex-1;
          this.scrollContent(this.totalWidth)
          this.$refs.swiper.insertBefore(this.cloneEls[this.currentIndex],this.currentImg)
        }

        // 3.添加定时器
        this.startTimer();
      },

      next: function (num) {
        // 1.移除定时器
        this.stopTimer();
        if(!this.scrolling){
          this.scrolling=true
          this.currentIndex =  this.currentIndex+1;
          this.scrollContent(-this.totalWidth);
          this.$refs.swiper.appendChild(this.cloneEls[this.currentIndex])
        }
        // 3.添加定时器

        this.startTimer();
      },
      ind_next(idx){
        if(!this.scrolling){
          this.scrolling=true
          this.currentIndex = idx;
          this.scrollContent(-this.totalWidth);
          this.$refs.swiper.appendChild(this.cloneEls[this.currentIndex])
        }
      },
      ind_previous(idx){
        if(!this.scrolling){
          this.scrolling=true
          this.swiperStyle.left=`-${this.totalWidth}px`
          this.currentIndex = idx;
          this.scrollContent(this.totalWidth)
          this.$refs.swiper.insertBefore(this.cloneEls[this.currentIndex],this.currentImg)
        }
      },
      indClick(index){
        this.stopTimer()
        if(index>this.currentIndex){
          this.ind_next(index)
        }
        else if(index<this.currentIndex){
          this.ind_previous(index)
        }
        this.startTimer();
      }
    }
	}
</script>

<style scoped>
  #hy-swiper {
    overflow: hidden;
    position: relative;
    height: 100%;
  }

  .swiper {
    display: flex;
    position: relative;
  }

  .indicator {
    display: flex;
    justify-content: center;
    position: absolute;
    width: 100%;
    bottom: 14px;
  }

  .indi-item {
    cursor: pointer;
    box-sizing: border-box;
    width: 16px;
    height: 16px;
    border-radius: 50%;
    background-color: #fff;
    line-height: 8px;
    text-align: center;
    font-size: 12px;
    margin: 0 8px;
    border: 1px solid rgba(0,0,0,.3);
  }
  .indi-item:hover{
    background-color: rgba(212,62,46,1.0);
  }
  .indi-item.active {
    background-color: rgba(212,62,46,1.0);
  }
  .left,.right{
    top:50%;
    position: absolute;
    z-index: 10;
    transform: translateY(-50%);
  }
  .left a,.right a{
    display: block;
    height: 73px;
    width: 42.5px;
  }
  .left a {
    background-image: url("~assets/img/xuebi.png");
    background-position-x: -85px;
  }
  .right a{
    background-image: url("~assets/img/xuebi.png");
    background-position-x:-125.5px ;
  }
  .left a:hover {
    background-image: url("~assets/img/xuebi.png");
    background-position-x: 0px;
  }
  .right a:hover{
    background-image: url("~assets/img/xuebi.png");
    background-position-x:-42.5px ;
  }
  .left{
    left: 0;
  }
  .right{
    right: 0;
  }
</style>
