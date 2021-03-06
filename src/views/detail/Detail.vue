<template>
  <div id="detail">
    <detail-nar-bar class="detail-nav"></detail-nar-bar>
    <scroll class="content">
      <detail-swiper :top-images = "topImages"/>
      <detail-base-info :goods = "goods" />
      <detail-shop-info :shop = "shop" />
      <detail-goods-info :detail-info = "detailInfo " />
      <detail-param-info :param-info = "paramInfo" />
      <detail-comment-info :comment-info = "commentInfo" />
    </scroll>
    <detail-bottom-bar @addCart="addToCart"/>

  </div>
</template>

<script>

import DetailNarBar from './childcomps/DetailNarBar'
import DetailSwiper from './childcomps/DetailSwiper'
import DetailBaseInfo from './childcomps/DetailBaseInfo'
import DetailShopInfo from './childcomps/DetailShopInfo'
import DetailGoodsInfo from './childcomps/DetailGoodsInfo'
import DetailParamInfo from './childcomps/DetailParamInfo'
import DetailCommentInfo from './childcomps/DetailCommentInfo'
import DetailBottomBar from './childcomps/DetailBottomBar'



import { getDetail, Goods, Shop, GoodsParam} from '../../network/detail'
import Scroll from '../../components/common/scroll/Scroll.vue'


  export default {
    name: 'Detail',
    components: {
      DetailNarBar,
      DetailSwiper,
      DetailBaseInfo,
      DetailShopInfo,
      Scroll,
      DetailGoodsInfo,
      DetailParamInfo,
      DetailCommentInfo,
      DetailBottomBar
    },
    data() {
      return {
        iid: null,
        topImages: [],
        goods: {},
        shop: {},
        detailInfo: {},
        paramInfo: {},
        commentInfo: {}
      }
    },
    created() {
      this.iid = this.$route.params.iid;

      getDetail(this.iid).then(res => {
        // 1.将res中数据创给轮播图
        // console.log(res);
        const data = res.result
        this.topImages = data.itemInfo.topImages,
        // 2.获取商品信息
        this.goods = new Goods(data.itemInfo, data.columns, data.shopInfo.services)
        // 3.店铺信息
        this.shop = new Shop(data.shopInfo)
        // 4.商品详情
        this.detailInfo = data.detailInfo
        // 5.参数信息
        this.paramInfo = new GoodsParam(data.itemParams.info, data.itemParams.rule)
        // 6.评论信息
        if (data.rate.cRate !== 0) {
          this.commentInfo = data.rate.list[0]
        }
      })
    },
    methods: {
      addToCart() {
        // 1.获取购物车需要展示的信息
        const product = {}
        product.images = this.topImages[0];
        product.title = this.goods.title;
        product.desc = this.goods.desc;
        product.price = this.goods.realPrice;
        product.iid = this.iid;
        product.count = 0

        // 2将商品添加到购物车
        // this.$store.cartList.push(this.product)
        this.$store.dispatch('addCart', product).then(res => {
          this.$toast.show(res, 2000)
        })


      }
    }
  }
</script>

<style scoped>
  #detail {
    position: relative;
    z-index: 999;
    background-color: #fff;
    height: 100vh;
  }
  .detail-nav {
    position: relative;
    z-index: 999;
    background-color: #fff;
  }
  .content {
    height: calc(100% - 44px);
  }
</style>