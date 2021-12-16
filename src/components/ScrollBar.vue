<template>
   <div class="scroll">
        <div class="scrollContent" :style="contentStyle">
            <slot></slot>
        </div>
        <div class="scrollBar" v-if="controll"><span :style="barStyle"></span></div>
    </div>
</template>

<script>
export default {
    name:"ScrollBar",
    data(){
        return{
            barStyle:{},
            contentStyle:{},
            controll:true,  //是否显示滚动条
            scrollTop:0,
            scrollWrapHeight:0,
            contentHeight:0,
            maxHeight:0
        }
    },
    methods:{
        init(){
            this.barStyle = {
                transition:'',
                transtorm:'translateY(0)'
            },
            this.contentStyle = {
                transition:'',
                transtorm:'translateY(0)'
            }
        }
    },
    mounted(){
        this.init();
    }
}
</script>

<style>
/* 滚动条样式 */
.scroll{
    position: relative;
    overflow: hidden;
}
.scrollContent{
    position: absolute;
    left: 0;
    top: 0;
}
.scrollBar{
    position: absolute;
    right: 0;
    top: 0;
    width: 6px;
    border-radius: 3px;
    background: rgba(200, 200, 200, .7);
    height: 100%;
}
.scrollBar span{
    position: absolute;
    width: 100%;
    height: 100px;
    background: rgba(0, 0, 0, .5);
    border-radius: 4px;
    left: 0;
    top: 0;
}
</style>