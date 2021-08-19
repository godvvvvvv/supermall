<template>
    <div class="goodslistitem">
        <img :src="goodsitem.show.img" alt="">
        <div class = "goodsinfo">
            <p>{{goodsitem.title}}</p>
            <span class="price">{{goodsitem.price}}</span>
            <span class="cfav">{{goodsitem.cfav}}</span>
        </div>
    </div>
</template>

<script>
    export default {
        name: "GoodsListitem",
        props:{
            goodsitem:{
                type:Object,
                default(){
                    return {}
                }
            }
        }
    }
</script>

<style scoped>
    .goodslistitem{
        padding-bottom: 40px;
        width: 48%;
        position: relative;
    }
    .goodslistitem img{
        width: 100%;
        border-radius: 5px;
    }
    .goodsinfo {
        font-size: 12px;
        position: absolute;
        bottom: 5px;
        left: 0;
        right: 0;
        overflow: hidden;
        text-align: center;
    }
    .goodsinfo p {
        overflow: hidden;
        text-overflow: ellipsis;
        white-space: nowrap;
        margin-bottom: 3px;
    }

    .goodsinfo .price {
        color: var(--color-high-text);
        margin-right: 20px;
    }

    .goodsinfo .cfav {
        position: relative;
    }

    .goodsinfo .cfav::before {
        content: '⭐';
        position: absolute;
        left: -15px;
        top: -1px;
        width: 7px;
        height: 7px;
        /*background: url("https://www.iconfont.cn/search/index?searchType=icon&q=%E6%98%9F%E6%98%9F") 0 0/14px 14px;*/
    }
</style>