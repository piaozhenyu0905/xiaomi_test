<template>
  <div class="wrapper-bottom-bar">
    <div class="bottom-bar">
      <bottom-left-bar></bottom-left-bar>
      <div class="img-bottom">
        <a href="#"><img src="https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/fc0f553382bb5143e667b284dfcf02db.jpg" alt=""></a>
      </div>
      <div class="img-bottom">
        <a href="#"><img src="https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/61bef947ca0b863003b3e68336192a3a.jpg?thumb=1&w=1533&h=575&f=webp&q=90" alt=""></a>
      </div>
      <div class="img-bottom">
        <a href="#"><img src="https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/918820682e4a490221cfd92b24c14b86.jpg?thumb=1&w=1533&h=575&f=webp&q=90" alt=""></a>
      </div>
    </div>
  </div>
</template>

<script>
import BottomLeftBar from "@/components/BottomLeftBar";
export default {
  name: "BottomNavBar",
  components:{
    BottomLeftBar
  }
}
</script>

<style scoped>
 .wrapper-bottom-bar{
   width: 100%;
   margin-top: 30px;
 }
  .bottom-bar{
    width: 1226px;
    margin:0 auto;
    display: flex;
    justify-content: space-between;
  }
  .img-bottom img{
    width: 316px;
    height: 170px;
  }
</style>