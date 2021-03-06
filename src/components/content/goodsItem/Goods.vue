<template>
  <div class="goods">
    <goods-item v-for="(item, index) in goods" :key="index" :goods-item="item" />
  </div>
</template>

<script>
import GoodsItem from './GoodsItem'

export default {
  name: 'Goods',
  props: {
    goods: {
      type: Array,
      default() {
        return [

        ]
      }
    }
  },
  components: {
    GoodsItem,
  }
}
</script>

<style>
  .goods {
    position: relative;
    display: flex;
    flex-wrap: wrap;
    padding: 2px;
  }
</style>