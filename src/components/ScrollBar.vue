<template>
   <div class="scroll" ref="scrollWrap">
        <div class="scrollContent" :style="contentStyle" ref="scrollContent">
            <slot></slot>
        </div>
        <div class="scrollBar" v-if="isShow" ref="scrollBar"><span :style="barStyle" @mousedown="barScroll($event)"></span></div>
    </div>
</template>

<script>
export default {
    name:"ScrollBar",
    data(){
        return{
            barStyle:{},
            contentStyle:{},
            isShow:true,    //是否显示滚动条
            scrollTop:0,    //滚动条走的距离
            scrollWrapHeight:0, //父级的高度
            contentHeight:0,    //内容的高度
            maxHeight:0,        //滚动条能够走的最大距离
            multiple:0,         //倍数
        }
    },
    methods:{
        init(){
            this.barStyle = {
                transition:'',
                transform:'translateY(0)'
            };
            this.contentStyle = {
                transition:'',
                transform:'translateY(0)'
            };
            
            this.scrollWrapHeight = this.$refs.scrollWrap.clientHeight;
            this.contentHeight = this.$refs.scrollContent.clientHeight;

            this.multiple = this.contentHeight/this.scrollWrapHeight;

            if(this.multiple<1){
                this.isShow = false;
                this.$refs.scrollWrap.onwheel = null;
                this.multiple = 1;
                return;
            }

            // 最大倍数不能超过20，要不太小了，用户就点不住了
            this.multiple = this.multiple > 20 ? 20 : this.multiple;

            this.$set(this.barStyle,'height', this.$refs.scrollBar.offsetHeight / this.multiple +"px");

            this.maxHeight = this.$refs.scrollBar.offsetHeight - this.$refs.scrollBar.offsetHeight / this.multiple;

        },
        barScroll(e){
            document.onmousemove = function(evt){
                
            }
        },

        // 滑动条的主体
        scroll(){
            if(this.llTop<0){
                this.scrollTop = 0;
            }
            if(this.scrollTop > this.maxHeight){
                this.scrollTop = this.maxHeight;
            }
            
            // let scaleY = this.scrollTop / this.maxHeight;
            this.$set(this.barStyle,'transform','translateY('+this.scrollTop+')');
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