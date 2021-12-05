<template>
  <div id="bg1" :style="'background:url('+ bannerBg.gwsbdt_12 + ') no-repeat center'"></div>
</template>

<script>
import $ from "jquery"
export default {
    name:"BannerBg",
    props:{
        bannerBg:Object
    }
}
</script>

<style>
#bg1{
    height: 650px;
    background: #fff url(~@/assets/images/bg_01.jpg) no-repeat center;
    margin-top: -134px;
}
</style>