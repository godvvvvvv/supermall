<template>
    <div class="backtop">
        <img src="@/assets/img/common/上箭头.png" alt="">
    </div>
</template>

<script>
    export default {
        name: "BackTop"
    }
</script>

<style scoped>
    .backtop {
        position: fixed;
        right: 8px;
        bottom: 53px;
    }
    .backtop img{
        width: 40px;
        height: 40px;
    }
</style>