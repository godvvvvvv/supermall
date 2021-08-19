<template>
    <div class="wrapper" ref="wrapper">
        <div class="aaaaa">
            <slot></slot>
        </div>
    </div>
</template>

<script>
    import BScroll from '@better-scroll/core'
    import Pullup from '@better-scroll/pull-up'

    BScroll.use(Pullup)

    export default {
        name: "Scroll",
        // components: {
        //     BScroll
        props: {
            checkposition: {
                type: Number,
                default: 0
            },
            pullUpLoad: {
                type: Boolean,
                default: false
            }
        },
        // },
        data() {
            return {
                bscroll: null
            }
        },
        mounted() {
            this.bscroll = new BScroll(this.$refs.wrapper, {
                observeDOM: true,
                click: true,
                probeType: this.checkposition,
                pullUpLoad: this.pullUpLoad,
            })
            //获取滑动位置
            this.bscroll.on('scroll', (position) => {
                this.$emit("getposition", position)
            })
            //上拉加载更多

            this.bscroll.on('pullingUp', () => {
                this.$emit('pullup')
                this.bscroll.refresh()
            })

        },
        methods: {
            backToTop(x, y, time) {
                this.bscroll.scrollTo(x, y, time)
            },
            finishpullup() {
                this.bscroll.finishPullUp()
            }
        }

    }
</script>

<style scoped>

</style>