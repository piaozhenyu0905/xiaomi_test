<template>
  <div class="phone-region">
    <div class="title">
      <h2>手机</h2>
      <div class="more">
        <a href="">
          查看更多
          <i class="fas fa-arrow-right"></i>
        </a>
      </div>
    </div>
    <div class="phone-menu">
      <div class="left-big-image pop">
        <a href=""><img :src="bigImg" alt=""></a>
      </div>
      <div class="right-phone-menu">
        <div class="phone-item pop" v-for="(item,index) in phones" :key="index">
          <a href="">
            <img :src="item.url" alt="">
            <div class="name">{{item.name}}</div>
            <div class="text">{{item.text}}</div>
            <div class="price">{{item.price}}</div>
          </a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "PhoneRegion",
  data(){
    return{
      bigImg:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/c583f2edc613f1be20fa415910b13ce3.jpg?thumb=1&w=293&h=768&f=webp&q=90',
      phones:[
        {name:'Redmi Note 11 Pro系列',text:'Redmi Note 11 Pro系列',price:'1799元起',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/6d0a3e7acc3e91e2cfd83dbbe1d1c029.jpg?thumb=1&w=250&h=250&f=webp&q=90'},
        {name:'Redmi Note 11 5G',text:'5000mAh大电量',price:'1199元起',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/50da95e9e4496dcac8704da2deb94f6e.jpg?thumb=1&w=250&h=250&f=webp&q=90'},
        {name:'Redmi Note 11 4G',text:'5000mAh大电量',price:'999元起',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/c001ebc4aee69bc9ff6fae9ecf9137d0.jpg?thumb=1&w=250&h=250&f=webp&q=90'},
        {name:'黑鲨4S Pro',text:'磁动力升降肩键',price:'4799元起',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/3490cfc52dc7c9abf9badfa1dc2d0eae.png?thumb=1&w=250&h=250&f=webp&q=90'},
        {name:'黑鲨4S',text:'磁动力升降肩键',price:'2699元起',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/7290b681343512c60e3a845379f3335f.jpg?thumb=1&w=250&h=250&f=webp&q=90'},
        {name:'Xiaomi Civi',text:'3200万高清质感自拍',price:'2599元起',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/c5c752522100ecd364cc53752bb660bc.jpg?thumb=1&w=250&h=250&f=webp&q=90'},
        {name:'Xiaomi MIX 4',text:'CUP全面屏',price:'4199元起',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/ab07e0fcbec3beb8b0f409db8bee8da4.jpg?thumb=1&w=250&h=250&f=webp&q=90'},
        {name:'Redmi Note 10 Pro',text:'天玑1100年度旗舰芯',price:'1499元起',url:'//cdn.cnbj1.fds.api.mi-img.com/mi-mall/61454401f855cf5ed64747a6ac04bae5.jpg?thumb=1&w=250&h=250&f=webp&q=90'}
      ]
    }
  }
}
</script>

<style scoped>
  .phone-region{
    margin-top: 30px;
  }
  .title{
    position: relative;
  }
  .title h2{
    font-size: 22px;
  }
  .title .more{
    position: absolute;
    top: 5px;
    right: 0;
  }
  .more a{
    transition: color 0.3s;
  }
  .more:hover a{
    color: #FF6700;
  }

  .phone-menu{
    margin-top: 30px;
    display: flex;
  }

  .left-big-image{
    width: 234px;
    height: 614px;
  }
  .left-big-image img{
    width: 100%;
    height: 100%;
    vertical-align: top;
  }
/*  右侧手机区*/
  .right-phone-menu{
    padding-left: 15px;
    width: 992px;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    align-content: space-between;
  }
  .phone-item{
    background-color: white;
    width: 234px;
    height: 300px;
    text-align: center;
    padding: 20px;
  }
  .phone-item a{
    display: block;
    width: 100%;
    height: 100%;
  }
  .phone-item img{
    width: 160px;
    height: 160px;
  }
  .phone-item .name{
    margin-top: 10px;
  }
  .phone-item .price{
    color: #FF6700;
    margin-top: 15px;
    font-size: 14px;
  }
  .phone-item .text{
    color: #b0b0b0;
    margin-top: 6px;
    font-size: 12px;
  }
/*  设置弹出效果*/
  .pop{
    transition: transform 0.3s;
  }
  .pop:hover{
    transform: translateY(-4px);
    box-shadow: 0 0 10px rgba(0,0,0,.2);
  }

</style>