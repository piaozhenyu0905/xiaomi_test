<template>
  <div id="hy-swiper">
    <div class="swiper" ref="swiper">
      <slot></slot>
    </div>
    <div class="right" @click="next">
      <a href="#"></a>
    </div>
    <div class="left" @click="previous">
      <a href="#"></a>
    </div>
    <slot name="indicator">
    </slot>
    <div class="indicator">
      <slot name="indicator" v-if="showIndicator && slideCount>1">
        <div v-for="(item, index) in slideCount" class="indi-item" :class="{active: index === currentIndex-1}" :key="index"
             @click="indClick(index)">
        </div>
      </slot>
    </div>
  </div>
</template>

<script>
export default {
  name: "TestSwiper",
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
      currentIndex: 1, // 当前的index
      scrolling: false, // 是否正在滚动
    }
  },

  mounted: function () {
    //为了解决异步与加载的冲突问题，不在mounted中进行初始化设置

    // 1.操作DOM, 在前后添加Slide
    // setTimeout(() => {
    //
    //   this.handleDom();
    //   // 2.开启定时器
    //   this.startTimer();
    // }, 300)  //这边有问题，因为异步请求的数据需要时间，故该值不能过小，否则模板渲染时数据还没传来
  },
  methods: {
    /**
     * 定时器操作
     */
    startTimer: function () {
      this.playTimer = setInterval(() => {
        this.currentIndex++;
        this.scrollContent(-this.currentIndex * this.totalWidth);
      }, this.interval)

    },
    stopTimer: function () {
      clearInterval(this.playTimer);
    },
    /**
     * 操作DOM, 在DOM前后添加Slide
     */
    handleDom: function () {
      console.log('handle')
      // 1.获取要操作的元素
      let swiperEl = this.$refs.swiper
      let slidesEls = swiperEl.getElementsByClassName('slide');

      // 2.保存个数
      this.slideCount = slidesEls.length;

      // 3.如果大于1个, 那么在前后分别添加一个slide
      if (this.slideCount > 1) {
        let cloneFirst = slidesEls[0].cloneNode(true); //深度复制节点
        let cloneLast = slidesEls[this.slideCount - 1].cloneNode(true);
        swiperEl.insertBefore(cloneLast, slidesEls[0]);
        swiperEl.appendChild(cloneFirst);
        this.totalWidth = swiperEl.offsetWidth;
        this.swiperStyle = swiperEl.style;
      }

      // 4.让swiper元素, 显示第一个(目前是显示前面添加的最后一个元素)
      this.setTransform(-this.totalWidth);
    },


    /**
     * 滚动到正确的位置
     */
    scrollContent: function (currentPosition) {
      // 0.设置正在滚动
      this.scrolling = true;

      // 1.开始滚动动画
      this.swiperStyle.transition ='transform '+ this.animDuration + 'ms';
      // console.log(this.swiperStyle.transition)
      this.setTransform(currentPosition); //这里设置translate
      // console.log(currentPosition)

      // 2.判断滚动到的位置
      this.checkPosition();

      // 4.滚动完成
      this.scrolling = false
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
      setTimeout(() => {
        // 1.校验正确的位置
        this.swiperStyle.transition = '0ms';
        if (this.currentIndex >= this.slideCount + 1) {
          this.currentIndex = 1;
          this.setTransform(-this.currentIndex * this.totalWidth);
        } else if (this.currentIndex <= 0) {
          this.currentIndex = this.slideCount;
          this.setTransform(-this.currentIndex * this.totalWidth);
        }

        // 2.结束移动后的回调
        this.$emit('transitionEnd', this.currentIndex-1); //暂时没用
      }, this.animDuration)
    },


    /**
     * 控制上一个, 下一个
     */
    previous: function () {
      this.changeItem(-1);
    },

    next: function () {
      this.changeItem(1);
    },

    changeItem: function (num) {
      // 1.移除定时器
      this.stopTimer();

      // 2.修改index和位置
      this.currentIndex += num;
      this.scrollContent(-this.currentIndex * this.totalWidth);

      // 3.添加定时器
      this.startTimer();
    },
    indClick(index){
      this.stopTimer()
      this.currentIndex=index+1
      this.scrollContent(-this.currentIndex * this.totalWidth);
      this.startTimer();
    }
  }
}
</script>

<style scoped>
#hy-swiper {
  /*overflow: hidden;*/
  position: relative;
  height: 100%;
}

.swiper {
  display: flex;
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
