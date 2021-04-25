<template>
  <div id="home">
    <nav-bar class="home-nav"><div slot="center">购物街</div></nav-bar>
    <home-swiper :banners="banners"/>
    <recommend-views :recommends="recommends"/>
  </div>
</template>

<script>
import NavBar from 'components/common/navbar/NavBar.vue'
import HomeSwiper from './childComps/HomeSwiper'
import RecommendViews from './childComps/RecommendViews'

import {getHomeMultidata} from 'network/home.js'

export default {
  name:'Home',
  components:{
    NavBar,
    HomeSwiper,
    RecommendViews
  },
  data(){
    return {
      // result:null
      banners:[],
      recommends:[]
    }
  },
  created(){
    getHomeMultidata().then(res=>{
      console.log(res)
      // this.result=res
      this.banners=res.data.banner.list
      this.recommends=res.data.recommend.list
    })
  }
}
</script>

<style>
  .home-nav{
    background-color: var(--color-tint);
    color: white;
  }
</style>