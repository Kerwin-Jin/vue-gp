<template>
  <div id="app">
    <Header/>
    <Nav/>
    <BannerBg :bannerBg="bannerImages"/>
    <Banner :bannerBg="bannerImages"/>
  </div>
</template>

<script>
import $ from "jquery"
import Header from "./views/head/Header"
import Nav from "./views/head/Nav"
import BannerBg from "./views/banner/BannerBg"
import Banner from "./views/banner/Banner"

export default {
  name:"App",
  components:{Header, Nav, BannerBg, Banner},
  data(){
    return {
      bannerImages:{}
    }
  },
  mounted(){
    this.getBannerBgData();
  },
  methods:{
    // 获取BannerBg背景照片
    getBannerBgData(){
      $.ajax({
        url:"https://gp.qq.com/zlkdatasys///data_zlk_gwsykvtst.json",
        dataType:'jsonp',
        jsonpCallback:'gwsycallback',
        success:(res)=>{
          console.log(res);
          this.bannerImages = res.gwsykv_18[0];
          // gwsykv_18:     banner图
          // mdtst_88: (6)  游戏特色里图片（大图）
          // tst_db: (6)    游戏特色里图片（小图）
        }
      })
    }
  }
}
</script>
<style>

</style>