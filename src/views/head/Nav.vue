<template>
  <!-- nav -->
  <div>
    <nav id="nav">
      <div class="nav1">
        <div class="title">
          <a href="#" target="_blank"
            ><img src="@/assets/images/logo2.png" alt=""
          /></a>
          <h1>和平精英<span>全球玩家的竞技冒险世界</span></h1>
        </div>
        <ul>
          <li v-for="item in navList.nav" :key="item.id"><a :href="item.link ? item.link : 'javascript:;'" :target="item.link ? '_blank' : ''">{{item.name}}</a></li>
        </ul>
        <div class="login">
          <span></span>
          <p>特种兵，请<span>登录</span></p>
        </div>
      </div>
      <div class="nav2">
        <ul>
          <li v-for="subNav in navList.subNav" :key="subNav.id">
            <ul>
              <li :class="nav.prefix" v-for="nav in subNav.nav" :key="nav.id"><a :href="nav.link ? nav.link : 'javascript:;'">{{nav.name}}</a></li>
            </ul>
          </li>
          <li>
            <ul class="contact">
              <li>
                <a href="javascript:;">官方公众号</a>
                <span><img src="@/assets/images/code1.png" alt="" /></span>
              </li>
              <li>
                <a href="javascript:;">微信用户社区</a>
                <span><img src="@/assets/images/code2.png" alt="" /></span>
              </li>
              <li>
                <a href="javascript:;">QQ用户社区</a>
                <span><img src="@/assets/images/code3.png" alt="" /></span>
              </li>
              <li>
                <a href="javascript:;">官方微博</a>
                <span><img src="@/assets/images/code4.png" alt="" /></span>
              </li>
            </ul>
          </li>
        </ul>
      </div>
    </nav>
  </div>
</template>

<script>
import navData from "@/data/nav.json"
export default {
    name:"Nav",
    data(){
        return{
            navList:{}
        }
    },
    mounted(){
        this.getNavData();
    },
    methods:{
        getNavData(){
            this.navList = navData;
        }
    }
};
</script>

<style>
/* nav start */
#nav {
  height: 134px;
  background: url(~@/assets/images/nav_bg.png) center no-repeat;
  position: relative;
}
#nav .nav1 {
  width: 1200px;
  margin: 0 auto;
  display: flex;
  position: relative;
  z-index: 2;
}
#nav .title {
  display: flex;
  margin-right: 40px;
}
#nav .title a {
  margin: 6px 20px 0 0;
}
#nav .title h1 {
  margin-top: 28px;
  font-size: 24px;
  position: relative;
  color: #ffb400;
}
#nav .title h1 span {
  font-size: 14px;
  color: #fff;
  display: block;
  font-weight: normal;
  margin-top: 2px;
}
#nav .title h1::after {
  content: "";
  width: 69px;
  height: 19px;
  position: absolute;
  top: 8px;
  right: -16px;
  background: url(~@/assets/images/new_version.png);
}

#nav .nav1 ul {
  display: flex;
}
#nav .nav1 ul a {
  display: block;
  width: 102px;
  height: 102px;
  text-align: center;
  line-height: 102px;
  color: #fff;
}
#nav .nav1 ul li a:hover {
  color: #ffb400;
}
#nav .nav1 ul li:last-child a {
  color: #ffb400;
  text-decoration: underline;
}

#nav .nav1 .login {
  position: absolute;
  width: 126px;
  height: 100px;
  right: -120px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

#nav .nav1 .login > span {
  width: 46px;
  height: 45px;
  background: url(~@/assets/images/dia-login-head.png) no-repeat;
  cursor: pointer;
}
#nav .nav1 .login p {
  color: #fff;
}
#nav .nav1 .login p span {
  color: #ffb400;
  cursor: pointer;
}

/* 当#nav hover的时候显示.nav2 */
#nav:hover .nav2 {
  height: 400px;
}

#nav .nav2 {
  position: absolute;
  width: 100%;
  height: 400px;
  background: rgba(0, 0, 0, 0.5);
  top: 0;
  left: 0;
  z-index: 1;
  height: 0;
  overflow: hidden;
  transition: height 0.3s ease;
}

#nav .nav2 > ul {
  width: 1100px;
  margin: 115px auto 0;
  display: flex;
  position: relative;
  left: 300px;
}
#nav .nav2 li li {
  width: 106px;
  height: 40px;
  line-height: 40px;
  font-size: 14px;
  text-align: center;
  position: relative;
}
#nav .nav2 a {
  color: #fff;
}
#nav .nav2 a:hover {
  color: #ffb400;
}
#nav .nav2 .new::before,
#nav .nav2 .hot::before {
  content: "N";
  width: 18px;
  height: 18px;
  line-height: 18px;
  background: #f31419;
  color: #fff;
  border-radius: 50%;
  font-size: 10px;
  position: absolute;
  top: 12px;
  left: 3px;
}

#nav .nav2 .hot::before {
  content: "H";
  left: 10px;
  top: 11px;
}
#nav .nav2 > ul li:nth-child(2) li:last-child::before {
  /* 第二列最后一个li */
  left: -3px;
}
#nav .nav2 > ul li:nth-child(4) li:first-child::before {
  /* 第四列第一个li */
  left: -10px;
}
#nav .nav2 > ul li:nth-child(5) li:nth-child(3):before {
  /* 第五列第3个li */
  left: 3px;
}
#nav .contact span {
  display: none;
  width: 132px;
  padding: 6px;
  background: #fff;
  position: absolute;
  left: -158px;
}
#nav .contact span::after {
  content: "";
  position: absolute;
  width: 0;
  height: 0;
  border-top: 10px solid #fff;
  border-right: 10px solid #fff;
  transform: rotate(45deg);
  right: -5px;
  top: 15px;
}
#nav .contact img {
  width: 100%;
}
#nav .contact li span {
  top: 0;
  right: 30px;
}
#nav .contact li:nth-child(3) span {
  background: #f0f0f0;
}
#nav .contact li:hover span {
  display: block;
}
</style>