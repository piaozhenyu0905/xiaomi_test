<template>
  <div class="rightcolomun">
    <ul class="menu-ul">
      <li v-for="(item,index) in menu_data" :key="index" class="formal">
        <div class="img-box">
          <img :src="item.imgUrlStatic" alt="" class="static" >
          <img :src="item.imgUrlHover" alt="" class="hover" >
        </div>
        <div class="menu-item">{{item.name}}</div>
      </li>
    </ul>
    <div class="back-top" @click="backTop" v-show="topDistance>1000">
      <div class="img-box">
        <img :src="backtop.imgUrlStatic" alt="" class="static" >
        <img :src="backtop.imgUrlHover" alt="" class="hover" >
      </div>
      <div class="menu-item">{{backtop.name}}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "rightColomunBar",
  mounted(){
    window.onscroll=()=>{
      console.log(window.scrollY)
      this.topDistance=window.scrollY
    }
  },
  data(){
    return {
      menu_data:[
        {
          imgUrlStatic:'https://i8.mifile.cn/b2c-mimall-media/98a23aae70f25798192693f21c4d4039.png',
          imgUrlHover:'https://i8.mifile.cn/b2c-mimall-media/74c4fcb4475af8308e9a670db9c01fdf.png',
          name:'手机APP'
        },
        {
          imgUrlStatic:'https://i8.mifile.cn/b2c-mimall-media/55cad219421bee03a801775e7309b920.png',
          imgUrlHover:'https://i8.mifile.cn/b2c-mimall-media/41f858550f42eb1770b97faf219ae215.png',
          name:'个人中心'
        },
        {
          imgUrlStatic:'https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/12eb0965ab33dc8e05870911b90f3f13.png',
          imgUrlHover:'https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/95fbf0081a06eec7be4d35e277faeca0.png',
          name:'售后服务'
        },
        {
          imgUrlStatic:'https://i8.mifile.cn/b2c-mimall-media/4f036ae4d45002b2a6fb6756cedebf02.png',
          imgUrlHover:'https://i8.mifile.cn/b2c-mimall-media/5e9f2b1b0da09ac3b3961378284ef2d4.png',
          name:'人工客服'
        },
        {
          imgUrlStatic:'https://i8.mifile.cn/b2c-mimall-media/d7db56d1d850113f016c95e289e36efa.png',
          imgUrlHover:'https://i8.mifile.cn/b2c-mimall-media/692a6c3b0a93a24f74a29c0f9d68ec71.png',
          name:'购物车'
        }
      ],
      touch_index:-1,
      backtop:{
          imgUrlStatic:'https://i1.mifile.cn/f/i/2018/home/totop.png',
          imgUrlHover:'https://i1.mifile.cn/f/i/2018/home/totop_hover.png',
          name:'回顶部'
      },
      topDistance:0
    }
  },
  methods:{
    MouseOver(index){
      this.touch_index=index
    },
    MouseOut(){
      this.touch_index=-1
    },
    backTop(){
      window.scrollTo({top:0})
    }

  }
}
</script>

<style scoped>
  .rightcolomun{
    z-index: 9999999;
    position: fixed;
    bottom: 60px;
    /*＋20px是为了不让菜单与内容贴边*/
    left: calc((100vw - 1226px) / 2 + 20px);
    margin-left: 1226px;
    background-color: #f5f5f5;
  }
  .menu-ul{
    width: 100%;
    text-align: center;
  }
  .menu-ul li{
    background-color: white;
    position: relative;
    padding:25px 15px;
    padding-top: 50px;
    border: rgba(0,0,0,.1) solid 1px;
    /*border-bottom:none;*/
    color:black;

  }
  .menu-ul li:last-child{
    border: rgba(0,0,0,.1) solid 1px;
  }

  .menu-ul li:hover .menu-item{
    color: #FF6700;
  }

  .static,.hover{
    position: absolute;
    top: 14px;
    left: 25px;
    height: 30px;
    width: 28px;
    transition: opacity 0.3s;
  }
  .static {
    opacity: 1;
  }
  .hover{
    opacity: 0;
  }
  .menu-ul li:hover .static{
    opacity: 0;
  }
  .menu-ul li:hover .hover{
    opacity: 1;
  }
  .menu-item{
    transition: color 0.3s;
    margin-top: 8px;
    font-size: 12px;
  }
  .back-top{
    text-align: center;
    margin-top: 20px;
    position: relative;
    padding:25px 15px;
    padding-top: 50px;
    border: rgba(0,0,0,.1) solid 1px;
    background-color: white;
    color:black;
  }
  .back-top:hover  .static{
    opacity: 0;
  }
  .back-top:hover  .hover{
   opacity: 1;
  }
  .back-top:hover .menu-item{
    color: #FF6700;
  }


</style>