<template>
  <div>
    <nav-bar >
      <div slot="left" class="back" @click="backClick">
        <img src="../../../assets/img/common/back.svg" alt="">
      </div>
      <div id="item" slot="center" class="narbar">
        <div v-for="(item, index) in titles" 
            :key="index" 
            class="title-item"
            :class="{active: currentindex === index}"
            @click="itemclick(index)">
          {{item}}
        </div>
      </div>
    </nav-bar>
  </div>
</template>

<script>

import NavBar from '../../../components/common/navbar/NarBar'


  export default {
    name: 'DetailNarbar',
    components: {
      NavBar
    },
    data () {
      return {
        titles: ['商品', '评论', '参数', '推荐'],
        currentindex: 0
      }
    },
    methods: {
      itemclick(index) {
        this.currentindex = index;
      },
      backClick() {
        this.$router.back()
      }
    }
  }
</script>

<style scoped>
  .narbar{
    display: flex;
  }
  .title-item{
    flex: 1;
    font-size: 14px;
  }
  .active{
    color: red;
  }
  .back{
    margin-top: 5px;
  }
</style>