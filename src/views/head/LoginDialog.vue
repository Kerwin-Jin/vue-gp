<template>
  <!-- 登录弹窗 -->
    <div id="loginBox" class="dialog" :class="{show:isShow}">
        <div class="wrap">
            <h3>登录</h3>
            <div class="btn">
                <a href="javascript:;">QQ登录</a>
                <a href="javascript:;">微信登录</a>
            </div>
            <button class="close" @click="$emit('close')"></button>
        </div>
    </div>
</template>

<script>
export default {
    name:"LoginDialog",
    props:{
        isShow:Boolean
    }
}
</script>

<style>
#loginBox .wrap{
    width: 634px;
    height: 327px;
    background: url(~@/assets/images/dia-login-bg.png) no-repeat center;
}
#loginBox .wrap .btn{
    display: flex;
    justify-content: center;
    align-items: center;
    margin-top: 40px;
}
#loginBox .btn a{
    width: 130px;
    height: 164px;
    font-size: 0;
    margin: 0 40px;
}
#loginBox .btn a:nth-child(1){
    background: url(~@/assets/images/dia-login-qq.png) no-repeat center;
}
#loginBox .btn a:nth-child(2){
    background: url(~@/assets/images/dia-login-wx.png) no-repeat center;
}
</style>