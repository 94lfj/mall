<template>
<div id="home">
  <nav-bar class="home-nav">
    <div slot="center">购物街</div>
  </nav-bar>
  <homeSwiper :banners="banners"/>
  <recommend-view :recommends="recommends"/>
  <feature></feature>
  <tab-control class="tab-control" :titles="['流行','新款','精选']" />
  <ul>
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
    <li></li>
  </ul>
</div>
</template>

<script>

import NavBar from "components/common/navbar/NavBar";
import TabControl from 'components/content/tabControl/TabControl'

import HomeSwiper from "./childComps/HomeSwiper";
import RecommendView from './childComps/RecommendView'
import Feature from './childComps/Feature'

import {getHomeMultidata} from "network/home";


export default {
  name: "Home",
  components: {
    NavBar,
    TabControl,
    HomeSwiper,
    RecommendView,
    Feature
  },
  data() {
    return {
      banners: [],
      recommends: []
    }
  },
  created() {
    //1、请求多个数据
    getHomeMultidata().then((res) => {
      this.banners = res.data.data.banner.list;
      this.recommends = res.data.data.recommend.list;
      console.log(this.banners);
    });
  }
}
</script>

<style scoped>
#home {
  padding-top: 44px;
}
.home-nav{
  background-color: var(--color-tint);
  color: white;
  position: fixed;
  left: 0;
  right: 0;
  bottom: 0;
  top: 0;
  z-index: 9;
}
.tab-control {
  position: sticky;
  top: 44px;
}
</style>
