<template>
  <div class="cart_list">
    <scroll class="content">
      <cart-list-item v-for="(item, index) in cartList" :key="index" :product="item"/>
    </scroll>
  </div>
</template>

<script>

import { mapGetters } from 'vuex'
import Scroll from '../../../components/common/scroll/Scroll'
import cartListItem from './cartListItem'



export default {
  name: 'cartList',
  components: {
    Scroll,
    cartListItem
  },
  computed: {
    ...mapGetters(['cartList'])
  },
  data () {
    return {
    }
  },
  methods: {

  }
}
</script>

<style scoped>
  .cart_list {
    height: calc(100% - 44px -49px);
  }
  .content {
    height: 100vh;
    overflow: hidden;
  }
</style>
