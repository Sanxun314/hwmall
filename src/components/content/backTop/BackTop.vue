<template>
  <div class="backtop" >
    <img src="../../../assets/img/common/top.png" alt="">
  </div>
</template>

<script>
export default {
  name: 'BackTop',
  methods: {
    // backClick() {
    //   console.log(1111);
    // }
  }

}
</script>

<style scoped>
 .backtop{
   position: fixed;
   right: 8px;
   bottom: 50px;
 }
 .backtop img{
   width: 40px;
   height: 40px;
 }
</style>