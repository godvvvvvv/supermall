<template>
    <div>
        <TabBar>
            <TabBarItem path = "/home" activecolor = "deeppink">
                <img slot="item-icon" src="@/assets/img/tabbar/首页.png" alt="">
                <img slot="item-icon-active" src="@/assets/img/tabbar/首页点击.png" alt="">
                <div slot="item-text">首页</div>
            </TabBarItem>
            <TabBarItem path = "/category" activecolor = "deeppink">
                <img slot="item-icon" src="@/assets/img/tabbar/分类.png" alt="">
                <img slot="item-icon-active" src="@/assets/img/tabbar/分类点击.png" alt="">
                <div slot="item-text">分类</div>
            </TabBarItem>
            <TabBarItem path = "/cart" activecolor = "deeppink">
                <img slot="item-icon" src="@/assets/img/tabbar/购物.png" alt="">
                <img slot="item-icon-active" src="@/assets/img/tabbar/购物车点击.png" alt="">
                <div slot="item-text">购物车</div>
            </TabBarItem>
            <TabBarItem path = "/profile" activecolor = "deeppink">
                <img slot="item-icon" src="@/assets/img/tabbar/我的.png" alt="">
                <img slot="item-icon-active" src="@/assets/img/tabbar/我的点击.png" alt="">
                <div slot="item-text">我的</div>
            </TabBarItem>
        </TabBar>
    </div>
</template>

<script>
    import TabBar from '../common/tabbar/TabBar'
    import TabBarItem from '../common/tabbar/TabBarItem'
    export default {
        name: "MainTabBar",
        components:{
            TabBar,
            TabBarItem
        }
    }
</script>

<style scoped>

</style>