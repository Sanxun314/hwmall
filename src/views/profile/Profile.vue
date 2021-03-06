<template>
  <div class="profile">
    <nar-bar class="p-bar">
      <div slot="center">我的</div>
    </nar-bar>
    <div class="loading">
      <span>登录</span>
    </div>
    <div class="wx">
      <img src="../../assets/img/profile/wx.svg" alt="">
      <div class="span">
        <span>微信登录</span>
      </div>
    </div>
    <div class="otloading">
      <span>其他方式登录</span>
    </div>
    <div class="dl">
      <ul>
        <li>
          <a href="#">
            <img src="../../assets/img/profile/170831_1078gd17460490lak5g7edbhah17i_90x90.png" alt="">
            <p>手机登录</p>
          </a>
        </li>
        <li>
          <a href="#">
            <img src="../../assets/img/profile/170831_68b918b6ikh668e8gibeg48bk82l3_90x90.png" alt="">
            <p>QQ登录</p>
          </a>
        </li>
        <li>
          <a href="#">
            <img src="../../assets/img/profile/170831_136567k82ideakd452d8db8ca27ak_90x90.png" alt="">
            <p>免密登录</p>
          </a>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import NarBar from '../../components/common/navbar/NarBar.vue'

  export default {
    components: { NarBar },
    name: 'Profile'

  }

</script>

<style scoped>
  .p-bar {
    background-color: #fca3cc;
    color: #fff;
  }
  .loading {
    font-weight: 400;
    font-size: 25px;
    color: black;
    margin-top: 70px;
    margin-left: 170px;
  }
  .wx {
    width: 315px;
    height: 49px;
    border-radius: 1rem;
    line-height: 1rem;
    background-color: rgb(9, 187, 7);
    margin-left: 40px;
    margin-top: 50px;
  }
  .wx img {
    width: 40px;
    height: 40px;
    margin: 5px 7px 0 70px ;
  }
  .span {
    float: right;
    line-height: 49px;
    margin-right: 120px;
    color: #fff;
  }
  .otloading {
    margin-top: 70px;
    margin-left: 137px;
  }
  .dl {
    width: 315px;
    height: 122px;
    margin-top: 70px;
    margin-left: 58px;
  }
  .dl li {
    list-style: none;
    float: left;
    padding: 20px;
  }
  .dl img {
    width: 44px;
    height: 44px;
  }
  .dl p{
    font-size: 12px;
  }
</style>