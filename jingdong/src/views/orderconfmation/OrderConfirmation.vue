<template>
<div class="wrapper">
    <div class="top">
        <div class="top__bgcor"></div>
        <div class="top__header">
            <div class="iconfont top__header__back">&#xe6f2;</div>
            确认订单
        </div>
        <div class="top__receiver">
            <div class="top__receiver__title">收获地址</div>
            <div class="top__receiver__address">背景理工大学国防科技园2皓龙</div>
            <div class="top__receiver__info">
                <span class="top__receiver__info__name">瑶妹 (先生)</span>
                <span class="top__receiver__info__name">111222333444</span>
            </div>
        </div>
        <div class="iconfont top__receiver__icon">&#xe6f2;</div>
    </div>
</div>
    
</template>


<script>
export default {
    name:'OrderConfirmation'
}

</script>

<style lang="scss" scoped>
.wrapper {
    position: absolute;
    left: 0;
    right: 0;
    bottom: 0;
    top: 0;
    background-color: #eee;

}


.top {
    position: relative;
    height: 1.96rem;
    background-size: 100% 1.59rem;
    background-image: linear-gradient(0deg,rgba(0,145,255,0.00)4%,#0091FF 50%);
    background-repeat: no-repeat;
    &__header {
        position: relative;
        padding-top: .26rem;
        height: .24rem;
        color: #FFF;
        text-align: center;
        font-size: .16rem;
        &__back {
            position:absolute;
            left: .18rem;
            font-size: .22rem;
        }
    }
    &__receiver {
        position: absolute;
        left: .18rem;
        right: .18rem;
        bottom: 0;
        height: 1.11rem;
        background: #FFF;
        border-radius: .04rem;
        &__title {
            padding: .16rem 0 .14rem .16rem;
            font-size: .16rem;
            color: #333;
            line-height: .22rem;
        }
        &__address {
            line-height: .2rem;
            padding: 0 .4rem 0 .16rem;
            font-size: .14rem;
            color: #333;

        }
        &__info {
            padding: .06rem 0 0 .16rem;
            &__name {
                line-height: .18rem;
                margin-right: .06rem;
                font-size: .12rem;
                color: #666;
            }
        }
        &__icon {
            transform: rotate(180deg);
            position: absolute;
            right: .16rem;
            top: .5rem;
            color: #666;
            font-size: .2rem;

        }
    }
}
</style>