<template>
  <div class="colomunSwiper">
    <swiper ref="Swiper">
      <swiper-item>
        <a href="#">
          <img src="https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/fc0f553382bb5143e667b284dfcf02db.jpg" alt="">
        </a>
      </swiper-item>
      <swiper-item>
        <a href="#">
          <img src="https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/61bef947ca0b863003b3e68336192a3a.jpg?thumb=1&w=1533&h=575&f=webp&q=90" alt="">
        </a>
      </swiper-item>
      <swiper-item>
        <a href="#">
          <img src="https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/918820682e4a490221cfd92b24c14b86.jpg?thumb=1&w=1533&h=575&f=webp&q=90" alt="">
        </a>
      </swiper-item>
      <swiper-item>
        <a href="#">
          <img src="https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/78d0483ed36158659fcf65a19a9b249a.jpeg?w=2452&h=920" alt="">
        </a>
      </swiper-item>
    </swiper>
  </div>
</template>

<script>
import {Swiper,SwiperItem} from '@/components/swiper/index'
export default {
  name: "colomunSwiper",
  components:{
    Swiper,
    SwiperItem
  },
  data(){
    return {
      banners:[]
    }
  },
  mounted() {
    this.$refs.Swiper.handleDom();
    this.$refs.Swiper.startTimer();
  }
}
</script>

<style scoped>
  .colomunSwiper{
    width:calc(1226px - 234px);
    height: 460px;
  }
</style>