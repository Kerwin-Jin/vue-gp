<template>
    <div class="download">
        <h3>扫码下载游戏</h3>
        <a href="#1" target="_blank">苹果下载</a>
        <a href="#2" target="_blank">安卓下载</a>
        <img src="@/assets/images/downqrcode.jpg" alt="">
    </div>
</template>

<script>
export default {

}
</script>

<style>
#banner .download{
    width: 180px;
    background: url(~@/assets/images/down_bg.png) no-repeat center;
    text-align: center;
}
#banner .download h3{
    font-size: 18px;
    line-height: 36px;
    color: #ffb007;
    font-weight: normal;
}
#banner .download a{
    display: block;
    height: 54px;
    margin-bottom: 5px;
    text-indent: -9999px;
    overflow: hidden;
}
#banner .download img{
    width: 160px;
}
</style>