<template>
  <div class="mid-nav-bar">
    <div class="nav-bar">
      <div class="left-home">
        <div class="img-box">
          <a href="#" class="home">
            <img src="~assets/img/home.png" alt="">
          </a>
          <a href="#" class="logo">
            <img src="~assets/img/logo.png" alt="">
          </a>
        </div>
      </div>
      <ul class="mid-item" @mouseleave="MouseLeave">
        <li v-for="(item,index) in menu " @mouseover="MouseOver(index)" class="pop" :class="{'active':index===currentIndex}"><a href="">{{item}}</a></li>
        <li><a href="" @mouseover="kickPop">服务</a></li>
        <li><a href="" @mouseover="kickPop">社区</a></li>
        <!--        创建一个弹出层-->
        <div class="goods-info">
          <pop-layer :goods="goods[currentIndex]"></pop-layer>
        </div>
      </ul>
      <form class="input-item">
        <div class="info">
          <span>Redmi Note8</span>
          <span>小米 9</span>
        </div>
        <input type="text" class="input-text">
        <button class="btn-logo">
          <i class="fas fa-search"></i>
        </button>
      </form>
    </div>
  </div>

</template>

<script>
import popLayer from "@/components/popLayer";
export default {
  name: "MidNavBar",
  components:{
    popLayer
  },
  data(){
    return {
        menu:['小米手机','Redmi 红米','电视','笔记本','家电','路由器','智能硬件'],
        currentIndex:-1,
        goods:[
            [
              {
              imgUrl:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/8cad77bda138fd94eadbc2ddfced7c56.png?thumb=1&w=200&h=138&f=webp&q=90',name:'Xiaomi civi',price:'2599元起',
              },
              {
                imgUrl:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/087c52d253d9301dff7743d6bf2d0330.png?thumb=1&w=200&h=138&f=webp&q=90',name:'Xiaomi MIX4',price:'4999元起',
              },
              {
                imgUrl:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/85e44ea2405ff8414148bbde7446b137.png?thumb=1&w=200&h=138&f=webp&q=90',name:'Xiaomi MIX FOLD',price:'7999元起',
              },
              {
                imgUrl:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/e3c5d99c28700a3c45ea65eebbea0a04.png?thumb=1&w=200&h=138&f=webp&q=90',name:'Xiaomi 11 Ultra',price:'5499元起',
              },
              {
                imgUrl:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/a1c45eadcedeb27b1cafca0359422da9.png?thumb=1&w=200&h=138&f=webp&q=90',name:'Xiaomi civi',price:'2599元起',
              },
              {
                imgUrl:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/56e3379b5422cb06e5c8a0c546445606.png?thumb=1&w=200&h=138&f=webp&q=90',name:'Xiaomi 11 青春饭',price:'1999元起',
              }
            ],
            [
              {
                imgUrl:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/e3c5d99c28700a3c45ea65eebbea0a04.png?thumb=1&w=200&h=138&f=webp&q=90',name:'Xiaomi 11 Ultra',price:'5499元起',
              },
              {
                imgUrl:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/a1c45eadcedeb27b1cafca0359422da9.png?thumb=1&w=200&h=138&f=webp&q=90',name:'Xiaomi civi',price:'2599元起',
              },
              {
                imgUrl:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/56e3379b5422cb06e5c8a0c546445606.png?thumb=1&w=200&h=138&f=webp&q=90',name:'Xiaomi 11 青春饭',price:'1999元起',
              }
            ],
            [
                {
              imgUrl:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/8cad77bda138fd94eadbc2ddfced7c56.png?thumb=1&w=200&h=138&f=webp&q=90',name:'Xiaomi civi',price:'2599元起',
            },
              {
                imgUrl:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/85e44ea2405ff8414148bbde7446b137.png?thumb=1&w=200&h=138&f=webp&q=90',name:'Xiaomi MIX FOLD',price:'7999元起',
              },
              {
                imgUrl:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/e3c5d99c28700a3c45ea65eebbea0a04.png?thumb=1&w=200&h=138&f=webp&q=90',name:'Xiaomi 11 Ultra',price:'5499元起',
              },
              {
                imgUrl:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/087c52d253d9301dff7743d6bf2d0330.png?thumb=1&w=200&h=138&f=webp&q=90',name:'Xiaomi MIX4',price:'4999元起',
              },

              {
                imgUrl:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/a1c45eadcedeb27b1cafca0359422da9.png?thumb=1&w=200&h=138&f=webp&q=90',name:'Xiaomi civi',price:'2599元起',
              },
              {
                imgUrl:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/56e3379b5422cb06e5c8a0c546445606.png?thumb=1&w=200&h=138&f=webp&q=90',name:'Xiaomi 11 青春饭',price:'1999元起',
              }],
            [
                {
              imgUrl:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/85e44ea2405ff8414148bbde7446b137.png?thumb=1&w=200&h=138&f=webp&q=90',name:'Xiaomi MIX FOLD',price:'7999元起',
            },
              {
                imgUrl:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/e3c5d99c28700a3c45ea65eebbea0a04.png?thumb=1&w=200&h=138&f=webp&q=90',name:'Xiaomi 11 Ultra',price:'5499元起',
              },],
            [
                {
              imgUrl:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/8cad77bda138fd94eadbc2ddfced7c56.png?thumb=1&w=200&h=138&f=webp&q=90',name:'Xiaomi civi',price:'2599元起',
            },
              {
                imgUrl:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/087c52d253d9301dff7743d6bf2d0330.png?thumb=1&w=200&h=138&f=webp&q=90',name:'Xiaomi MIX4',price:'4999元起',
              },
              {
                imgUrl:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/85e44ea2405ff8414148bbde7446b137.png?thumb=1&w=200&h=138&f=webp&q=90',name:'Xiaomi MIX FOLD',price:'7999元起',
              },
              {
                imgUrl:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/e3c5d99c28700a3c45ea65eebbea0a04.png?thumb=1&w=200&h=138&f=webp&q=90',name:'Xiaomi 11 Ultra',price:'5499元起',
              },
              {
                imgUrl:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/a1c45eadcedeb27b1cafca0359422da9.png?thumb=1&w=200&h=138&f=webp&q=90',name:'Xiaomi civi',price:'2599元起',
              },
              {
                imgUrl:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/56e3379b5422cb06e5c8a0c546445606.png?thumb=1&w=200&h=138&f=webp&q=90',name:'Xiaomi 11 青春饭',price:'1999元起',
              }],
            [
              {
                imgUrl:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/087c52d253d9301dff7743d6bf2d0330.png?thumb=1&w=200&h=138&f=webp&q=90',name:'Xiaomi MIX4',price:'4999元起',
              },
              {
                imgUrl:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/85e44ea2405ff8414148bbde7446b137.png?thumb=1&w=200&h=138&f=webp&q=90',name:'Xiaomi MIX FOLD',price:'7999元起',
              },
              {
                imgUrl:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/e3c5d99c28700a3c45ea65eebbea0a04.png?thumb=1&w=200&h=138&f=webp&q=90',name:'Xiaomi 11 Ultra',price:'5499元起',
              },
              {
                imgUrl:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/a1c45eadcedeb27b1cafca0359422da9.png?thumb=1&w=200&h=138&f=webp&q=90',name:'Xiaomi civi',price:'2599元起',
              },
              {
                imgUrl:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/8cad77bda138fd94eadbc2ddfced7c56.png?thumb=1&w=200&h=138&f=webp&q=90',name:'Xiaomi civi',price:'2599元起',
              },

              {
                imgUrl:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/56e3379b5422cb06e5c8a0c546445606.png?thumb=1&w=200&h=138&f=webp&q=90',name:'Xiaomi 11 青春饭',price:'1999元起',
              }
            ],
            [
              {
                imgUrl:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/087c52d253d9301dff7743d6bf2d0330.png?thumb=1&w=200&h=138&f=webp&q=90',name:'Xiaomi MIX4',price:'4999元起',
              },

              {
                imgUrl:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/e3c5d99c28700a3c45ea65eebbea0a04.png?thumb=1&w=200&h=138&f=webp&q=90',name:'Xiaomi 11 Ultra',price:'5499元起',
              },
              {
                imgUrl:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/a1c45eadcedeb27b1cafca0359422da9.png?thumb=1&w=200&h=138&f=webp&q=90',name:'Xiaomi civi',price:'2599元起',
              },
            ]
        ]
    }
  },
  methods:{
    MouseOver(index){
      this.currentIndex=index
    },
    MouseLeave(){
      this.currentIndex=-1
    },
    kickPop(){
      this.currentIndex=-1
    }
  }
}
</script>

<style scoped>
  li{
    flex-shrink: 0;
  }
  .mid-nav-bar{
    width: 100%;
    /*margin: 20px 0;*/
    position: relative;

  }
  .nav-bar{
    margin:0 auto;
    width: 1226px;
    height: 100px;
    line-height: 100px;
    display: flex;
    align-items: center;
  }
  /*左侧图标*/
  .left-home img{
    width: 54px;
    height: 54px;
    vertical-align: top;
  }
  .left-home{
    width: 54px;
    height: 54px;
    overflow: hidden;
  }
  .img-box{
    display: flex;
    transition: transform 0.2s;
  }
  .left-home:hover .img-box{
    transform: translateX(-54px);
  }
/*  中间导航栏*/
  .mid-item{
    margin-left: 180px;
    display: flex;
  }
  .active ~.goods-info{
    height: 230px;
  }

  .mid-item a{
    display: block;
    margin-right: 20px;
  }
  .active a{
    color:#FF6700;
  }
  .mid-item a:hover{
    color:#FF6700;
  }
  .goods-info{
    transition: height 0.3s;
    overflow: hidden;
    position: absolute;
    height: 0;
    width: 100%;
    top: 100px;
    left: 0;
    z-index: 9999999;
    box-shadow: 0 1px 3px rgba(0,0,0,.3);
    background-color: white;
  }
/*  右侧输入框*/
  .input-item{
    display: flex;
    height: 50px;
    position: relative;
    margin-left: 80px;
    outline: none;
  }
  .input-text{
    padding:10px;
    width: 264px;
    border: 1px solid rgb(224,224,224);
  }
  .input-text:focus{
    border-color: #FF6700;
    outline: none;
  }
  .input-text:focus+.btn-logo{   /*这里要用+，即相邻兄弟选择器*/
    border-color: #FF6700;
  }
  .info{
    position: absolute;
    top:-25px;
    left:120px;
    outline: none;
  }
  .info span{
    font-size: 14px;
    background-color: rgb(224,224,224);
    margin-right: 10px;
  }
  .btn-logo{
    transition: background-color 0.2s;
    background: #fff;
    position: relative;
    height: 50px;
    width: 50px;
    border: 1px solid rgb(224,224,224);
  }
  .btn-logo:hover{
    background-color:#FF6700;
    border-color: #FF6700;
  }
  .btn-logo i{
    position: absolute;
    top: 17px;
    right: 0;
    bottom: 0;
    left: -1px;
    margin:auto;
  }

</style>