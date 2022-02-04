<template>
   <div class="scroll" ref="scrollWrap" @wheel.prevent="wheel($event)">
        <div class="scrollContent" :style="contentStyle" ref="scrollContent">
            <slot></slot>
        </div>
        <div class="scrollBar" v-if="control" ref="scrollBar" @mousedown="scrollBarClick($event)">
            <span :style="barStyle" @mousedown.prevent.stop="barScroll($event)"></span>
        </div>
    </div>
</template>

<script>
export default {
    name:"ScrollBar",
    data(){
        return{
            barStyle:{},        // 滚动条样式
            contentStyle:{},    // 内容样式
            control:true,       //是否显示滚动条
            scrollTop:0,        //滚动条走的距离
            scrollWrapHeight:0, //父级的高度
            contentHeight:0,    //内容的高度
            maxHeight:0,        //滚动条能够走的最大距离
            multiple:0,         //倍数
        }
    },
    methods:{
        init(){

            // 初始化样式
            this.barStyle = {
                transition:'',
                transform:'translateY(0)'
            };
            this.contentStyle = {
                transition:'',
                transform:'translateY(0)'
            };
            
            // 设置滑块高度
            this.scrollWrapHeight = this.$refs.scrollWrap.offsetHeight;
            this.contentHeight = this.$refs.scrollContent.offsetHeight;

            // console.log(this.scrollWrapHeight,this.contentHeight);

            this.multiple = this.contentHeight / this.scrollWrapHeight;
            // console.log(this.multiple);

            if(this.multiple<1){
                this.control = false;
                this.$refs.scrollWrap.onwheel = null;
                this.multiple = 1;
                return;
            }

            // 最大倍数不能超过20，要不太小了，用户就点不住了
            this.multiple = this.multiple > 20 ? 20 : this.multiple;

            this.$set(this.barStyle,'height', this.$refs.scrollBar.offsetHeight / this.multiple +"px");

            // this.maxHeight = this.$refs.scrollBar.offsetHeight - parseInt(this.barStyle.height);
            this.maxHeight = this.$refs.scrollBar.offsetHeight - this.$refs.scrollBar.offsetHeight / this.multiple;
        },
        barScroll(e){
            let startY = e.clientY;
            let startT = parseInt(this.barStyle.transform.split("(")[1]);

            this.barStyle.transition = this.contentStyle.transition = null;
            // this.$set(this.barStyle,'transition',null);
            // this.$set(this.contentStyle,'transition',null);
            // bar.style.transition = scrollContent.style.transition = null;

            document.onmousemove = (e)=>{
                this.scrollTop = e.clientY - startY + startT;
                this.scroll();
            }

            document.onmouseup = ()=>document.onmousemove = null;

            // e.preventDefault();
            // e.stopPropagation();
        },
        // 滑动条的主体
        scroll(){
            if(this.scrollTop < 0){
                this.scrollTop = 0;
            }
            if(this.scrollTop > this.maxHeight){
                this.scrollTop = this.maxHeight;
            }
            
            let scaleY = this.scrollTop / this.maxHeight;

            this.barStyle.transform = 'translateY('+this.scrollTop +'px)';
            this.contentStyle.transform = 'translateY('+(this.scrollWrapHeight - this.contentHeight) * scaleY +'px)';

            // this.$set(this.barStyle,'transform','translateY('+this.scrollTop+')');
            // this.$set(this.contentStyle,'transform',)
        },

        // 点击滑动
        scrollBarClick(e){
            this.scrollTop = e.clientY - this.$refs.scrollBar.getBoundingClientRect().top - (parseFloat(this.barStyle.height)/2);
            this.barStyle.transition = this.contentStyle.transition = '.3s';
            // bar.style.transition = scrollContent.style.transition = '.3s';
            // this.$set(this.barStyle, 'transition','.3s');
            // this.$set(this.contentStyle, 'transition','.3s');
            this.scroll();
        },


        // 滚轮功能
        wheel(e){
            e.deltaY > 0 ? this.scrollTop += 50 : this.scrollTop -= 50;
            this.barStyle.transition = this.contentStyle.transition = '.3s';
            this.scroll();
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