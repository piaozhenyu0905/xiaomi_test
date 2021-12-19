<template>
  <ul class="phoneUl">
    <li v-for="(item,index) in goods" :key="index">
      <a href="">
        <img :src="item.imgUrl" alt="">
        <div class="goods-name">{{item.name}}</div>
        <div class="goods-price">{{item.price}}</div>
      </a>
    </li>
  </ul>
</template>

<script>
export default {
  name: "popLayer",
  data(){
    return {
    }
  },
  props:{
    goods:{}
  }

}
</script>

<style scoped>
  .phoneUl{
    display: flex;
    width: 80%;
    margin:40px auto;

  }
  .phoneUl li{
    position: relative;
    line-height: 1;
    width: 204px;
    height: 201px;
    text-align: center;
  }
  .phoneUl img{
    width: 160px;
    height: 110px;
  }
  li:not(:last-of-type)::after{
    content: '';
    position: absolute;
    width: 1px;
    top: -5px;
    right: 0;
    height: 110px;
    background-color:rgba(0,0,0,.2)
  }

  .goods-name{
    font-size: 12px;
    margin-top: 17px;
  }
  .goods-price{
    font-size: 12px;
    margin-top: 5px;
    color:#FF6700;
  }
</style>