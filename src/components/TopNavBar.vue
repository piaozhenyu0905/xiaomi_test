<template>
  <div class="topNavBar ">
    <div class="topBar">
      <ul class="Item-ul-left">
              <li><a href="javascript:;" class="h">小米商城</a></li>
              <li class="line">|</li>
              <li><a href="javascript:;" class="h">MIUI</a></li>
              <li class="line">|</li>
              <li><a href="javascript:;" class="h">LOT</a></li>
              <li class="line">|</li>
              <li class="service-li">
                <a href="javascript:;" class="h">云服务
                  <ul class="service">
                    <li class="ser-item">阿里云</li>
                    <li class="ser-item">腾讯云</li>
                    <li class="ser-item">百度云</li>
                    <li class="ser-item">华为云</li>
                  </ul>
                </a>
              </li>
              <li class="line">|</li>
              <li><a href="javascript:;" class="h">金融</a></li>
              <li class="line">|</li>
              <li><a href="javascript:;" class="h">有品</a></li>
              <li class="line">|</li>
              <li><a href="javascript:;" class="h">小爱开放平台</a></li>
              <li class="line">|</li>
              <li><a href="javascript:;" class="h">企业团购</a></li>
              <li class="line">|</li>
              <li><a href="javascript:;" class="h">资质证照</a></li>
              <li class="line">|</li>
              <li><a href="javascript:;" class="h">协议规则</a></li>
              <li class="line">|</li>
              <li class="qrode-li">
                <a href="javascript:;" class="h">
                下载APP
                <div class="qrode">
                  <a href="#">
                    <img src="~assets/img/erwei.png" alt="">
                    <div class="qrode-text">小米商城APP</div>
                  </a>
                </div>
              </a>
              </li>
              <li class="line">|</li>
              <li><a href="javascript:;" class="h">Selection Location</a></li>
      </ul>
      <ul class="Item-ul-right">
        <li class="item-shopcart">
          <a href="javascript:;">
            <i class="fas fa-shopping-cart"></i>
            购物车</a>
        </li>
        <li><a href="javascript:;" class="h">消息通知</a></li>
        <li class="line">|</li>
        <li><a href="javascript:;" class="h">注册</a></li>
        <li class="line">|</li>
        <li><a href="javascript:;" class="h">登录</a></li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "TopNavBar",
  data(){
    return {
      top_data:['小米商城','MIUI','LOT','云服务','金融','有品','小爱开放平台','企业团购','资质证照','协议规则','下载APP','Selection Location']
    }
  },

}
</script>

<style scoped>
  a{
    font-size: 14px;
    color: #b0b0b0;
    display: block;
    height: 40px;
  }
  a:hover{
    color: #fff;
  }
  li{
    flex-shrink: 0;
  }
  .line{
    margin:-1px 8px 0;
    opacity: 0.5;
  }
  /*外部容器*/
  .topNavBar{
    height: 40px;
    line-height: 40px;
    background-color: #333;
    width: 100%;
  }
  /*内部容器居中于外部，且宽度固定*/
  .topBar{
    margin:0 auto;
    width: 1226px;
    display: flex;
    justify-content: space-between;
  }
  /*左侧导航*/
  .Item-ul-left{
    position: relative;
    display: flex;
  }
  /*右侧导航*/
  .Item-ul-right{
    display: flex;
    flex-direction: row-reverse;
    position: relative;
  }
  /*购物车*/
  .item-shopcart{
    background-color: #424242;
    width: 120px;
    text-align: center;
    margin-left: 20px;
    height: 40px;
  }
  .item-shopcart a:hover{
    background-color: white;
    color:#FF6700;
  }

  /*二维码*/
  .qrode-li{
    position: relative;
    overflow: hidden;
  }
  .qrode-li:hover{
    overflow: visible;
  }
  .qrode-li:hover .qrode{
    height: 146px;
  }
  /*小三角箭头*/
  .qrode-li:hover::after{
    display: block;
  }
  .qrode-li::after{
    display:none;
    content: '';
    height: 0;
    width: 0;
    border:7px solid;
    border-color:transparent transparent white transparent;
    bottom: 0;
    left: 20px;
    border-top: none;
    position: absolute;
  }
  .qrode{
    transition: height 0.4s;
    position: absolute;
    overflow: hidden;
    height: 0;
    left: -20px;
    box-shadow: 0 1px 5px rgba(0,0,0,.5);
    line-height: 1;
    padding: 15px;
    z-index:99999;
    background-color: #fff;
  }
  .qrode img{
    width: 90px;
    height: 90px;
  }
  .qrode-text{
    margin-top: 10px;
    position: relative;
    left:2px;
  }
  .qrode a{
    color:black;
  }
  .qrode a:hover{
    color:black;
  }

/*  下拉菜单*/
  .service-li{
    position: relative;
  }
  .service-li:hover .service{
      display: block;
  }
  .service-li:hover .ser-item{
    color: black;
  }
  .service-li:hover::after{
    display: block;
  }
  .service-li::after{
    display:none;
    content: '';
    height: 0;
    width: 0;
    border:7px solid;
    border-color:transparent transparent white transparent;
    bottom: 0;
    left: 15px;
    border-top: none;
    position: absolute;
  }
  .service{
    display: none;
    z-index: 9999999999999;
    position: absolute;
    width: 80px;
    left: -20px;
    text-align: center;
    box-shadow: 0 2px 4px rgba(0,0,0,.2);
  }
  .ser-item{
    background-color:#fff;
  }
  .ser-item:hover{
    background-color:#FF6700;
    color:white;
  }
</style>