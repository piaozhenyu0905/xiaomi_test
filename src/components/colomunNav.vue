<template>
  <div class="colomun-wrapper">
    <div class="colomunNav">
      <colomun-item-nav ></colomun-item-nav>
      <colomun-swiper ></colomun-swiper>
    </div>
  </div>
</template>

<script>
import colomunItemNav from "@/components/colomun/colomunItemNav";
import colomunSwiper from "@/components/colomun/colomunSwiper";

export default {
  name: "colomunNav",
  components:{
    colomunItemNav,
    colomunSwiper,

  },
  data(){
    return{
    }
  },
  methods:{
  }
}
</script>

<style scoped>
.colomun-wrapper{
  width: 100%;

}
.colomunNav{
  position: relative;
}
.colomunNav{
  width: 1226px;
  margin:0 auto;
  display: flex;
}
</style>