<template>
    <!-- 底部导航栏部分 -->
  <div class="docker">
   <div 
   v-for="(item,index) in dockerList"
   :class="{'docker__item':true,'docker__item--active':(index === 0)}"
   :key="item.icon" 
   >
   <!-- 使用v-html防止转义 vue 中特殊符号会转义 -->
    <div class="iconfont" v-html="item.icon" />
    <div class="docker__title">{{item.text}}</div> 
    </div>
  </div>
</template>

<script>
import { registerRuntimeCompiler } from '@vue/runtime-core';
export default {
    name:'Docker',
    setup() {
        const dockerList = [
            {icon:'&#xe6f3;',text:'首页'},
            {icon:'&#xe7e5;',text:'购物车'},
            {icon:'&#xe61e;',text:'订单'},
            {icon:'&#xe660;',text:'我的'}
        ];
        return {
            dockerList
        }
    }

}
</script>

<style lang="scss" scoped>
// scoped 使该组件下的style标签只对该组件下的内容生效
@import '../../style/_Viriables.scss';

// 底部导航栏
.docker {
  display: flex;
  box-sizing: border-box;
  position: absolute;
  padding: 0 .18rem;
  left: 0;
  bottom: 0;
  width: 100%;
  height: 0.49rem;
  border-top: .01rem solid $content-bgColor;
  color: $content-fontColor;

  &__item {
    flex: 1;
    text-align: center;
    .iconfont {
      margin: .07rem 0 .02rem 0;
      font-size: .18rem;
    }
    &--active {
      color: #1FA4FC;
    }
  }
  &__title {
     font-size: .2rem;
    transform: scale(.5,.5);
    transform-origin: center top;
  }
}

</style>