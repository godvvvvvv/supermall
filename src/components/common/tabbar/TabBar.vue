<template>
    <div id="tab-bar">
       <slot></slot>
    </div>
</template>

<script>
    export default {
        name: "TabBar"
    }
</script>

<style scoped>
    #tab-bar {
        display: flex;
        background-color: rgba(144, 143, 169, 1);
        position: fixed;
        left: 0;
        right: 0;
        bottom: 0;
        box-shadow: 0px -3px 1px rgba(100, 100, 100, 0.2);
        z-index: 9;
    }

</style>