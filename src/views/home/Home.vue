<template>
    <div id="myhome">
        <NavBar class="navbar">
            <div slot="center">购物街</div>
        </NavBar>

        <BScroll class="content" ref="bscroll" @getposition="backtophidden" @pullup = "pullup"
                 :checkposition = "3" :pullUpLoad = "true" >

            <HomeSwiper :banners="banners"></HomeSwiper>
            <RecommendView :recommends="recommends"></RecommendView>
            <FeatuerView></FeatuerView>
            <TabControl :titles="['流行','精选','新款']" class="tabcontrol" @tabclick="tabclick"></TabControl>
            <GoodsList :goods="showgoods"></GoodsList>

        </BScroll>
        <div>呵呵呵呵</div>

        <BackTop class="backtop" @click.native="backclick" v-show="isShow"></BackTop>

    </div>
</template>

<script>
    import HomeSwiper from './childrencomps/HomeSwiper';
    import RecommendView from './childrencomps/RecommendView'
    import FeatuerView from './childrencomps/FeatuerView'

    import TabControl from '@/components/content/tabcontrol/TabControl'
    import NavBar from '@/components/common/navbar/NavBar'
    import GoodsList from '@/components/content/goods/GoodsList'
    import BScroll from '@/components/common/scroll/Scroll'
    import {gethomemultidata, getGoodsmultidata} from '@/network/home'
    import BackTop from '@/components/content/backtop/BackTop'
    import index from "../../store";


    export default {
        name: "Home",
        components: {
            NavBar,
            HomeSwiper,
            RecommendView,
            FeatuerView,
            TabControl,
            GoodsList,
            BScroll,
            BackTop
        },
        data() {
            return {
                banners: [],
                recommends: [],
                goods: {
                    'pop': {page: 0, list: []},
                    'new': {page: 0, list: []},
                    'sell': {page: 0, list: []}
                },
                currenttype: 'pop',
                isShow:false
            }
        },
        computed: {
            showgoods() {
                return this.goods[this.currenttype].list
            }
        },
        created() {
            this.gethome1();
            this.gethome2('pop')
            this.gethome2('new')
            this.gethome2('sell')
        },
        methods: {
            gethome1() {
                gethomemultidata().then(res => {
                    this.banners = res.data.banner.list;
                    this.recommends = res.data.recommend.list
                })
            },
            gethome2(type) {
                const page = this.goods[type].page + 1
                getGoodsmultidata(type, page).then(res => {
                    this.goods[type].list.push(...res.data.list);
                    this.goods[type].page += 1
                    this.$refs.bscroll.finishpullup()
                })
            },
            tabclick(index) {
                switch (index) {
                    case 0:
                        this.currenttype = 'pop'
                        break
                    case 1:
                        this.currenttype = 'new'
                        break
                    case 2:
                        this.currenttype = 'sell'
                        break
                }
            },
            backclick() {
                this.$refs.bscroll.backToTop(0, 0, 500)
            },
            backtophidden(position) {
               this.isShow =  (-position.y) > 1000
            },
            pullup(){
                this.gethome2(this.currenttype)
            }
        }
    }
</script>

<style scoped>
    #myhome {
        height: 100vh;
        position: relative;
    }

    .navbar {
        background-color: var(--color-tint);
        color: var(--color-background);
        position: fixed;
        left: 0;
        right: 0;
        top: 0;
        z-index: 9;
    }

    .tabcontrol {
        position: sticky;
        top: 44px;
        z-index: 8;
    }

    .content {
        /*height: calc(100% - 93px);*/
        /*overflow: hidden;*/
        overflow: hidden;

        position: absolute;
        top: 44px;
        bottom: 49px;
        left: 0;
        right: 0;
    }

</style>