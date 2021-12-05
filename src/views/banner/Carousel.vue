<template>
  <div class="carousel">
    <ul class="carouselInner">
      <li>
        <a href="#"><img src="@/assets/images/pic_01.jpeg" alt="" /></a>
      </li>
      <li>
        <a href="#"><img src="@/assets/images/pic_02.jpeg" alt="" /></a>
      </li>
    </ul>
    <div class="carouselIndicators">
      <span class="active"></span>
      <span></span>
    </div>
  </div>
</template>

<script>
export default {
    name:"Carousel"
};
</script>

<style>
#banner .carousel{
    width: 590px;
}
#banner .carouselInner{
    width: 200%;
}
#banner .carouselIndicators{
    right:17px;
    bottom: 15px;
}
#banner .carouselIndicators span{
    width: 20px;
    height: 8px;
    margin: 7px;
    transition: width .2s linear;
}
#banner .carouselIndicators span:hover,#banner .carouselIndicators span.active{
    width: 40px;
}
</style>