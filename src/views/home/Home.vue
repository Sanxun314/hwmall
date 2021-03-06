<template>
  <div id="home">
    <nar-bar class="home-nav"><div slot="center">购物街</div></nar-bar>

    <scroll class="content" ref="scroll">
      <home-swiper :banners="banners"/>
      <recommend-view :recommend="recommend"/>
      <feature-view />
      <tab-contral class="tab-contral" :title="['精选', '好货' , '低价']" @Eclick="Eclick"></tab-contral>
      <goods :goods="goods[currentType].list"/>
    </scroll>

    <back-top @click.native="backClick" />

  </div> 
</template>

<script>
  import HomeSwiper from './childComps/HomeSwiper'
  import RecommendView from './childComps/RecommendView'
  import FeatureView from './childComps/FeatureView'

  import NarBar from '../../components/common/navbar/NarBar'
  import TabContral from '../../components/content/tabContral/TabContral'
  import Goods from '../../components/content/goodsItem/Goods'
  import Scroll from '../../components/common/scroll/Scroll'
  import BackTop from '../../components/content/backTop/BackTop'

  import {getHomeMultidata, getHoemGoods} from '../../network/home.js'
  

  export default {
    name: 'Home',
    components: {
      HomeSwiper,
      RecommendView,
      FeatureView,
      NarBar,
      TabContral,
      Goods,
      Scroll,
      BackTop,
    },
    data() {
      return {
        banners: [],
        recommend: [],
        goods: {
          'pop': {page: 0, list: []},
          'new': {page: 0, list: []},
          'sell': {page: 0, list: []},
        },
        currentType: 'pop',
      }
    },
    created() {
      // 请求多个数据
      this.getHomeMultidata()

      // 请求goods数据
      this.getHoemGoods('pop')
      this.getHoemGoods('new')
      this.getHoemGoods('sell')
      
    },
    methods: {
      Eclick(index) {
        switch (index) {
          case 0:
            this.currentType = 'pop'
            break
          case 1:
            this.currentType = 'new'
            break
          case 2:
            this.currentType = 'sell'
            break
        }
      },
      backClick() {
        this.$refs.scroll.scroll.scrollTo(0, 0, 500)
      },


      // ---------------网络请求方法----------------------
      getHomeMultidata() {
        getHomeMultidata().then(res => {
          this.banners = res.data.banner.list
          this.recommend = res.data.recommend.list
        })
      },
      getHoemGoods(type) {
        const page = this.goods[type].page + 1
        getHoemGoods(type, page).then(res => {
          this.goods[type].list.push(...res.data.list)
          this.goods[type].page += 1
        })
      }
    }

  }

</script>

<style scoped>
  #home{
    padding-top: 44px;
    position: relative;
  }
  .home-nav{
    background-color: pink;
    color: #fff;
    font-size: 18px;
    position: fixed;
    left: 0;
    right: 0;
    top: 0;

    z-index: 9;
  }
  .tab-contral{
    position: sticky;
    top: 44px;z-index: 9;
  }
  .content{
    /* height: 300px; */
    /* overflow: hidden; */
    position: absolute;
    top: 44px;
    bottom: 49px;
    left: 0;
    right: 0;
  }
</style>