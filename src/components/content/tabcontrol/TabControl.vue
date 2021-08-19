<template>
    <div class="tabcontrol">
        <div v-for="(item,index) in titles"
             class="item"
             :class="{active:index==currentindex}"
             @click = "itemclick(index)">
            <span>{{item}}</span>
        </div>
    </div>
</template>

<script>
    import index from "../../../store";

    export default {
        name: "TabControl",
        props: {
            titles: {
                type: Array,
                default() {
                    return []
                }
            }
        },
        data() {
            return {
                currentindex: 0
            }
        },
        methods:{
            itemclick(index){
                this.currentindex = index
                this.$emit('tabclick',index)
            }
        }
    }
</script>

<style scoped>
    .tabcontrol {
        display: flex;
        text-align: center;
        height: 40px;
        line-height: 40px;
        font-size: 15px;
        width: 100%;
        background-color: white;
    }
    .item {
        flex: 1;
    }
    .item span{
        padding: 5px;
    }
    .active {
        color: var(--color-high-text);
    }
    .active span{
        border-bottom: 3px  solid var(--color-tint);
    }
</style>