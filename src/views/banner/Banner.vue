<template>
  <div id="banner" :style="'background:url('+bannerBg.gwxbdt_37+') no-repeat center'">
    <div class="container">
        <Tips/>
        <Top/>
    </div>
  </div>
</template>

<script>
import Tips from './Tips';
import Top from "./Top"
export default {
    components: { Tips,Top },
    name:"Banner",
    props:{
        bannerBg:Object
    }
};
</script>

<style>
/* banner start */
#banner {
  height: 562px;
  padding-top: 20px;
  background: #fff url(~@/assets/images/bg_02.jpg) no-repeat center;
}
#banner .container {
  width: 1200px;
  margin: 0 auto;
  position: relative;
}
</style>