<template>
    <div class="goodslist">
       <GoodsListitem v-for="(item,index) in goods" :goodsitem = "item" :key="index"></GoodsListitem>
    </div>
</template>

<script>
    import GoodsListitem from './GoodsListitem'
    export default {
        name: "GoodsList",
        components:{
          GoodsListitem
        },
        props:{
            goods:{
                type:Array,
                default(){
                    return []
                }
            }
        }
    }
</script>

<style scoped>
    .goodslist {
        display: flex;
        flex-wrap: wrap;
        justify-content: space-around;

        padding: 2px;
    }

</style>