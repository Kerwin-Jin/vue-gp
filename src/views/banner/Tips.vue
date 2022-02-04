<template>
    <div>
        <button class="tip" @click="toggleDialog">适龄提示</button>
        <!-- 适龄弹窗 -->
        <div id="yearBox" class="dialog" :class="{show:isVisible}">
            <div class="wrap">
                <h3>适龄提示</h3>
                <ScrollBar v-if="isVisible">
                    <h4>提示说明：</h4>
					<p>1、本游戏是一款玩法复杂的射击类游戏，适用于年满16周岁及以上的用户，建议未成年人在家长监护下使用游戏产品。</p>
					<p>2、本游戏背景为特种兵训练，画面风格写实、人物和场景丰富多样，有丰富的音效来烘托游戏氛围。游戏主要玩法为需要多人进行的团队竞技，玩法基于较复杂的思维判断和操作，对玩家的逻辑思维和团队协作能力有一定要求，鼓励玩家在训练中不断提升和挑战自我。游戏中有基于语音和文字的陌生人社交系统，但社交系统的管理遵循相关法律法规。</p>
					<p>3、本游戏中有用户实名认证系统，认证为未成年人的用户将接受以下管理：
					游戏中部分玩法和道具需要付费。未满8周岁的用户不能付费；8周岁以上未满16周岁的未成年人用户，单次充值金额不得超过50元人民币，每月充值金额累计不得超过200元人民币；16周岁以上的未成年人用户，单次充值金额不得超过100元人民币，每月充值金额累计不得超过400元人民币。<br>
					未成年人用户每日22点到次日8点不得使用，法定节假日每天不得使用超过3小时，其他时间每天不得使用超过1.5小时。</p>
					<p>4、游戏在3D场景中的竞技和操作训练有助于锻炼玩家的手眼协调能力、空间感知能力和快速反应能力，基于团队的玩法可以提升玩家的沟通能力、团队协作能力和大局观，鼓励玩家互帮互助，维持良好的社群关系。</p>
                </ScrollBar>
                <button class="close" @click="toggleDialog"></button>
            </div>
        </div>
    </div>
  
</template>

<script>
import ScrollBar from '@/components/ScrollBar.vue';
export default {
    components: { ScrollBar },
    name:"Tips",
    data(){
        return{
            isVisible:false
        }
    },
    methods:{
        toggleDialog(){
            this.isVisible = !this.isVisible;
        }
    }
}
</script>

<style>
#banner .tip{
    width: 119px;
    height: 154px;
    background: url(~@/assets/images/year-btn.png) no-repeat center;
    position: absolute;
    left: -135px;
    top:0;
    text-indent: -9999px;
    overflow: hidden;
}

#yearBox .wrap{
    width: 674px;
    height: 613px;
    background: url(~@/assets/images/year-hint.png) no-repeat center;
}
#yearBox .scroll{
    width: 610px;
    height: 470px;
    margin: 50px auto 0;
}
#yearBox .scrollContent{
    width: 584px;
    font-size: 20px;
    color: #535353;
    line-height: 33px;
}
#yearBox .scrollContent p{
    margin-bottom: 40px;
}
#yearBox .scrollContent h4{
    font-weight: normal;
    font-size: 22px;
    color: #ffb400;
}
</style>