<template>
  <div id="category">
    <nar-bar class="c-bar"><div slot="center">分类</div></nar-bar>
    <div class="left">
      <ul>
        <li 
          class="items" 
          :class="{active: currentIndex === index}" 
          v-for="(item, index) in title" 
          :key="index" 
          @click="itemclick(index)">
          {{item}}
        </li>
      </ul>
    </div>
    <div class="right">
      <div class="img">
        <a href="#">
          <img src="../../assets/img/fl/f1.jpeg" alt="">
        </a>
      </div>
    </div>
  </div>
</template>

<script>

  import NarBar from '../../components/common/navbar/NarBar.vue'


  export default {
    name: 'Category',
    components: {
      NarBar
    },
    data() {
      return {
        title: ['推荐分类', '女装', '鞋靴', '裤子', '冬装', '袜子', '帽子', '围巾', '手套', '冬装', '袜子', '帽子', '围巾'],
        currentIndex: 0,
      }
    },
    created() {
      
    },
    methods: {
      
    }

  }

</script>

<style scoped>
  .c-bar {
    background-color: #f2d974;
    color: #fff;
    margin-bottom: 10px;
  }
  .active {
    color: red;
  }
  .left {
    width: 25%;
  }
  .items {
    padding: 10px;
    background-color: #f2d974;
    border-radius: 8%;
    text-align: center;
    margin-bottom: 5px;
  }
  .right {
    width: 65%;
    /* background-color: pink; */
    float: right;
    margin-right: 10px;
  }
  .img img{
    width: 100%;
  }
</style>