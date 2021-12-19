<template>
  <div class="item-menu">
    <div class="item" v-for="(item,index) in good">
      <a href="">
        <img :src="item.url" alt="">
        <span>{{item.name}}</span>
      </a>
    </div>
  </div>
</template>

<script>
export default {
  name: "colomunItemMenu",
  data(){
    return{

    }
  },
  props:{
    good:[]
  }
}
</script>

<style scoped>
  .item-menu{
    position: absolute;
    top: 0px;
    left: 234px;
    z-index: 9999999999;
    display: flex;
    width:calc(1226px - 234px);
    height: 460px;
    background-color: white;
    box-shadow: 0 0 5px rgba(0,0,0,.3);
    flex-wrap: wrap;
    flex-direction: column;
    padding:0 15px;
  }
  .item{
    width: 25%;
    height: 16.6%;
    display: flex;
  }
  .item:hover span{
    color:#FF6700;
  }
  a{
    width: 100%;
    display: flex;
    align-items: center;
  }
  .item img{
    height: 40px;
    width: 40px;
  }
  .item span{
    font-size: 14px;
    margin-left: 15px;
  }
</style>