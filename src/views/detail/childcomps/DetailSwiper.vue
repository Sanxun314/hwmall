<!-- 我的页面 -->
<template>
    <swiper class="swiper-item">
      <swiper-item v-for="(item, index) in topImages" :key="index">
        <img :src="item" alt="">
      </swiper-item>
    </swiper>
</template>

<script>
// 这里可以导入其他文件（比如：组件，工具js，第三方插件js，json文件，图片文件等等）
// 例如：import 《组件名称》 from '《组件路径》'
  import {Swiper, SwiperItem} from '../../../components/common/swiper'

export default {
  // import引入的组件需要注入到对象中才能使用
  name: 'DetailSwiper',
  props: {
    topImages: {
      type: Array,
      default() {
        return []
      }
    }
  },
  components: {
    Swiper,
    SwiperItem
  },
  data () {
    // 这里存放数据
    return {

    }
  },
  // 方法集合
  methods: {

  }
}
</script>

<style scoped>
  .swiper-item {
    height: 300px;
    overflow: hidden;
  }
</style>
