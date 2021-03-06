<template>
  <div class="cart">

    <!-- 导航 -->
    <nar-bar class="cart-bar">
      <div slot="center">购物车({{$store.state.cartList.length}})</div>
    </nar-bar>

    <!-- 商品列表 -->
    <cart-list></cart-list>



    <!-- 底部 -->
    <cart-bottom-bar></cart-bottom-bar>

  </div>
</template>

<script>
import NarBar from '../../components/common/navbar/NarBar.vue'



import cartList from './childComps/cartList'
import CartBottomBar from './childComps/CartBottomBar'


  export default {
    components: {
      NarBar,
      cartList,
      CartBottomBar
    },
    name: 'Cart'

  }

</script>

<style scoped>
  .cart-bar {
    color: #fff;
    background-color: #bedbbb;
    font-weight: 700;
  }


</style>