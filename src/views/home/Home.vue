<template>
  <div id="home">
    <nav-bar class="home-nav"><div slot="center">购物街</div></nav-bar>
    <home-swiper :banners="banners"/>
    <recommend-views :recommends="recommends"/>
    <feature-view/>
    <tab-control class="tab-control" :titles="['流行','新歌','精选']"/>
    <goods-list :goods="goods['pop'].list"/>
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
import HomeSwiper from './childComps/HomeSwiper'
import RecommendViews from './childComps/RecommendViews'
import FeatureView from './childComps/FeatureView'

import NavBar from 'components/common/navbar/NavBar.vue'
import TabControl from 'components/content/tabControl/TabControl.vue'
import GoodsList from 'components/content/goods/GoodsList.vue'

import { getHomeMultidata,getHomeGoods } from 'network/home.js'

export default {
  name:'Home',
  components:{
    HomeSwiper,
    RecommendViews,
    FeatureView,
    NavBar,
    TabControl,
    GoodsList
  },
  data(){
    GoodsList
    return {
      // result:null
      banners:[],
      recommends:[],
      goods:{
        'pop':{page:0,list:[]},
        'new':{page:0,list:[]},
        'sell':{page:0,list:[]}
      }
    }
  },
  created(){
    this.getHomeMultidata();

    this.getHomeGoods('pop');
    this.getHomeGoods('new');
    this.getHomeGoods('sell');
  },
  methods:{
    getHomeMultidata(){
      getHomeMultidata().then(res=>{
      // console.log(res)
      // this.result=res
      this.banners=res.data.banner.list
      this.recommends=res.data.recommend.list
    })
    },
    getHomeGoods(type){
      const page=this.goods[type].page+1;
      getHomeGoods(type,page).then(res=>{
        console.log(res)
        this.goods[type].list.push(...res.data.list)
      })
    }
  }
}
</script>

<style>
  #home{
    padding-top: 44px;
  }
  .home-nav{
    background-color: var(--color-tint);
    color: white;

    position: fixed;
    left: 0px;
    right: 0px;
    top: 0px;
    z-index: 10;
  }
  .tab-control{
    position:sticky;
    top: 44px;
  }
</style>