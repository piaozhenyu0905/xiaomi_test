<template>
  <div class="bottom-region ">
    <div class="region-content">
      <div class="k40">
        <a href="">
          <img src="//cdn.cnbj1.fds.api.mi-img.com/mi-mall/f334fbd05d5681bb838fefd1c815d88c.jpg?thumb=1&w=1533&h=150&f=webp&q=90" alt="">
        </a>
      </div>
      <phone-region></phone-region>
    </div>
  </div>
</template>

<script>
import PhoneRegion from "@/components/PhoneRegion";
export default {
  name: "BottomRegion",
  components:{
    PhoneRegion
  }
}
</script>

<style scoped>
  .bottom-region{
    margin-top: 30px;
    background-color: #f5f5f5;
    height: 1500px;
  }
  .bottom-region::before{
    content: '';
    display: table;
    clear: both;
  }

  .region-content{
    margin:0 auto;
    width: 1226px;
  }
  .k40{
    margin-top: 20px;
  }
  .k40 img{
    width: 100%;
    vertical-align: top;
  }
</style>