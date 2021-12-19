<template>
  <div class="bottom-left-bar">
    <div class="item">
      <a href="#">
        <span>小米秒杀</span>
        </a>
     </div>
    <div class="item">
      <a href="#"><span>企业团购</span></a>
      </div>
    <div class="item">
      <a href="#"><span>F码通道</span></a>
      </div>
    <div class="item">
      <a href="#"><span>米粉卡</span></a>
      </div>
    <div class="item">
      <a href="#"><span>以旧换新</span></a>
      </div>
    <div class="item">
      <a href="#"><span>话费充值</span></a>
    </div>
  </div>
</template>

<script>
export default {
  name: "BottomLeftBar"
}
</script>

<style scoped>
.bottom-left-bar{
  width: 234px;
  height: 170px;
  background-color: #5f5750;
  font-size: 14px;
  display: flex;
  flex-wrap: wrap;
  padding-left:5px;
  padding-top: 2px;
}
.bottom-left-bar .item{
  position: relative;
}
.bottom-left-bar .item:hover a{
  color:white;
}
.bottom-left-bar a{
  color: #b0b0b0;
  width: 76px;
  height: 84px;
  display: block;
  position: relative;
  text-align: center;
}
.bottom-left-bar a span{
  position: absolute;
  left: 0;
  right: 0;
  margin:20px auto;
}
.bottom-left-bar a::before{
  content: '';
  width: 64px;
  height: 1px;
  background-color: #b0b0b0;
  opacity: 0.2;
  position: absolute;
  top: 1px;
  left: 6px;
}
.bottom-left-bar a::after{
  content: '';
  width: 1px;
  height: 70px;
  background-color: #b0b0b0;
  position: absolute;
  top: 6px;
  left: 0;
  opacity: 0.2;
}
</style>