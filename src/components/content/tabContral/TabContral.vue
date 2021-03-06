<template>
  <div class="tab-contral">
    <div v-for="(item, index) in title" 
    :key="item.index" class="tab-contral-item" 
    :class="{active: currentIndex === index }" 
    @click="itemclick(index)">
      <span>{{item}}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TabContral',
  props: {
    title: {
      type: Array,
      default() {
        return [

        ]
      }
    }
  },
  methods: {
    itemclick(index) {
      this.currentIndex = index
      this.$emit('Eclick', index)
    },
    
  },
  data() {
    return {
      currentIndex: 0
    }
  }
  
}
</script>

<style scopped>
  .tab-contral{
    display: flex;
    text-align: center;
    font-size: 15px;
    background-color: #fff;
    z-index: 9;
  }
  .tab-contral-item{
    flex: 1;
    height: 40px;
    line-height: 40px;
  }
  .active{
    color: pink;
  }
  .active span{
    border-bottom: 3px solid pink;
    padding: 5px;
  }
</style>