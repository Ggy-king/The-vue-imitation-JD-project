<template>
<div class="wrapper">
    <div class="search">
        <div 
        class="search__back iconfont"
        @click="handleBackClick"
        >
            &#xe6f2;
        </div>
        <div class="search__content">
            <span class="search__content__icon iconfont">
                &#xe62d;
            </span>
            <input 
            class="search__content__input"
            placeholder="请输入商品名称"
             />
        </div>
    </div>
    <ShopInfo 
    :item="item"
    :hideBorder="true"
    v-show="item.imgUrl"
    />
    <Content
    :shopName="item.name"
    />
    <!-- <Cart /> -->
</div>
</template>


<script>
import {reactive,toRefs} from 'vue'
import { useRouter,useRoute } from 'vue-router'
import {get} from '../../utils/request'
import ShopInfo from '../../components/ShopInfo'
import Content from './Content.vue'
// import Cart from './Cart'



// 这个是获取当前商铺信息 主要是路由传值的应用
const useShopInfoEffect = () => {
        const route = useRoute()
        const data = reactive({item:{}})
         const getItemData = async () => {
            const result = await get(`/api/shop/${route.params.id}`)
            if(result?.errno === 0 && result?.data){
                data.item = result.data
            }
        }
        const {item} = toRefs(data)
        return {item,getItemData}
}


// 获取回退功能实现
const useBackRouterEffect = () => {
    const router = useRouter()
    const handleBackClick = () => {
        router.back()
    }
    return handleBackClick
}




export default {
    name:'Shop',
    components: { ShopInfo , Content },
    // 要精简代码到setup位控制流程的一个函数
    setup() {
        const {item,getItemData} = useShopInfoEffect()
        const handleBackClick = useBackRouterEffect()
        getItemData()
        return {item,handleBackClick}
    }

}

</script>

<style lang="scss" scoped>
@import '../../style/Viriables';
.wrapper{
    padding: 0 .18rem;
}
.search {
    display: flex;
    margin: .14rem 0 .04rem 0;
    line-height: .32rem;
    &__back {
        width: .3rem;
        font-size: .24rem;
        color: #B6B6B6;
    }
    &__content {
        display: flex;
        flex: 1;
        background: $search-bgColor;
        border-radius: .16rem;
        &__icon {
            width: .44rem;
            text-align: center;
            color: $search-fontColor;
        }
        &__input {
            display: block;
            width: 100%;
            padding-right: .2rem;
            border: none;
            outline: none;
            height: .32rem;
            font-size: .14rem;
            color: $content-fontColor;
            &::placeholder {
                color: $content-fontColor;
            }
        }
    }
}
</style>


