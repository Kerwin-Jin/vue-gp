<template>
  <div class="top">
      <Download/>
      <Carousel/>
      <News/>
  </div>
</template>

<script>
import Carousel from './Carousel'
import Download from './Download'
import News from './News'
export default {
    name:"Top",
    components: { Download, Carousel, News }
}
</script>

<style>
#banner .top{
    display: flex;
    height: 320px;
}
</style>