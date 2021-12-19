<template>
  <div id="app">
    <top-nav-bar></top-nav-bar>
    <mid-nav-bar></mid-nav-bar>
    <colomun-nav></colomun-nav>
    <bottom-nav-bar></bottom-nav-bar>
    <right-colomun-bar></right-colomun-bar>
    <bottom-region></bottom-region>
  </div>
</template>

<script>
import TopNavBar from "@/components/TopNavBar";
import MidNavBar from "@/components/MidNavBar";
import colomunNav from "@/components/colomunNav";
import BottomNavBar from "@/components/BottomNavBar";
import rightColomunBar from "@/components/rightColomunBar";
import BottomRegion from "@/components/BottomRegion";


export default {
  name: 'App',
  components: {
    TopNavBar,
    MidNavBar,
    colomunNav,
    BottomNavBar,
    rightColomunBar,
    BottomRegion
  }
}
</script>

<style>
@import '~assets/css/base.css';

</style>
