<template>
  <div id="home">
    <Navbar class="home-nav"><div slot="center">购物街</div></Navbar>
    <home-swipper :banners="banners"></home-swipper>
    <recommend-view :recommends="recommends"></recommend-view>
    <feture-view></feture-view>
    <tab-control :titles="['流行','新款','精选']"></tab-control>
    <ul>
      <li>1</li>
      <li>2</li>
      <li>3</li>
      <li>4</li>
      <li>5</li>
      <li>6</li>
      <li>7</li>
      <li>8</li>
      <li>9</li>
      <li>0</li>
      <li>-</li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
    </ul>
  </div>
</template>

<script>
import HomeSwipper from './childComp/HomeSwipper.vue'
import RecommendView from './childComp/RecommendView.vue'
import FetureView from './childComp/FetureView.vue'

import Navbar from 'components/common/navbar/Navbar.vue'
import TabControl from 'components/content/tabControl/TabControl'

import { getHomeMultidata } from 'network/home.js'

export default {
  name: "MyHome",
  components: {
    HomeSwipper,
    RecommendView,
    FetureView,
    Navbar,
    TabControl,
    TabControl
  },
  data () {
    return {
      banners: [],
      recommends: []
    }
  },
  created () {
    getHomeMultidata().then(res => {
      this.banners = res.data.banner.list
      this.recommends = res.data.recommend.list
    })
  }
}
</script>

<style scoped>
  .home-nav {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    background-color: var(--color-tint);
    color: #fff;
    z-index: 9;
  }

  #home {
    padding-top: 44px;
  }
</style>
