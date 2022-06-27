<template>
  <div id="home">
    <Navbar class="home-nav"><div slot="center">购物街</div></Navbar>
    <home-swipper :banners="banners"></home-swipper>
    <recommend-view :recommends="recommends"></recommend-view>
  </div>
</template>

<script>
import Navbar from 'components/common/navbar/Navbar.vue'
import HomeSwipper from './childComp/HomeSwipper.vue'
import RecommendView from './childComp/RecommendView.vue'

import { getHomeMultidata } from 'network/home.js'

export default {
  name: "MyHome",
  components: {
    Navbar,
    HomeSwipper,
    RecommendView
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
    background-color: var(--color-tint);
    color: #fff;
  }
</style>
