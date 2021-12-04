<template>
  <header id="top">
        <div class="container">
            <div class="left">
                <a href="#" target="_blank" class="logo"><img src="@/assets/images/logo.png" alt=""></a>
                <span>
                    <img src="@/assets/images/img_01.jpg" alt="">
                    <a href="#" target="_blank"><img src="@/assets/images/img_02.jpg" alt=""></a>
                </span>
            </div>
            <div class="right">
                <h3 class="text1"><a href="#">成长守护平台</a></h3>
                <h3 class="text2">
                    <span>腾讯游戏排行榜</span>
                    <iframe src="https://game.gtimg.cn/images/js/title/title_game_rank.html?rd=5079157561030598" frameborder="0"></iframe>
                </h3>
            </div>
        </div>
    </header>
</template>

<script>
export default {
    name:"Header"
}
</script>

<style>
/* header start */
#top{
    height: 40px;
    background: #fff;
    border-bottom: 1px solid #f5f5f5;
}
#top .container{
    width: 980px;
    margin: 0 auto;
    display: flex;
    justify-content: space-between; /*两端对齐*/
}

#top .left{
    position: relative;
}

#top .logo{
    margin:0 20px;
    position: relative;
    z-index: 4;
}

#top .left span a{
    position: absolute;
    left: 0;
    top: 0;
    padding: 0 3px 3px;
    border-bottom: 1px solid #eee;
    display: none;
    z-index: 3;
}
#top .left span:hover a{
    display: block;
}

#top .right{
    position: relative;
    display: flex;
}
#top .right h3{
    line-height: 40px;
    font-size: 14px;
    font-weight: normal;
    color: #464646;
}
#top .right h3 a{
    color: #464646;
}
#top .right h3 a:hover{
    color: #ff4e00;
}

#top h3.text1{
    margin-right: 20px;
    padding-left: 30px;
}
#top h3.text1::before{
    content: "";
    width: 30px;
    height: 30px;
    background: url('~@/assets/images/ico_01.png') -30px 0;
    position: absolute;
    left: 0;
    top: 5px;
}
#top h3.text2{
    padding-right: 30px;
    cursor: pointer;
}
#top h3.text2::after{
    content: "";
    width: 30px;
    height: 30px;
    background: url('~@/assets/images/ico_01.png');
    position: absolute;
    right: 0;
    top: 5px;
    opacity: .1;
    transform: rotate(90deg);
}

#top .right iframe{
    position: absolute;
    right: 0;
    top: 40px;
    display: none;
    width: 708px;
    height: 582px;
    z-index: 4;
}
#top h3.text2:hover iframe{
    display: block;
}
/* header end*/
</style>