<template>
<div id="home">
  <van-Nav-bar title = "购物街" class = "home-nav-bar" fixed/>

  <scroll class="content">
    <van-swipe :autoplay="3000">
      <van-swipe-item v-for="(image, index) in banners" :key="index">
       <img v-lazy="image.image" class="img-swipe"/>
       </van-swipe-item>
    </van-swipe>
    <home-recommend-view :recommends="recommends"></home-recommend-view>
    <feature-view></feature-view>
    <tab-control class="tab-control" :titles="['流行', '新款', '精选']" @tabClick="tabClick"></tab-control>
    <goods-list :goods="goods[currentType].list"></goods-list>
  </scroll>
  <!-- <p>{{timeMsg}}</p> -->
  <div class="a"></div>
  
</div>


</template>

<script>
import {getHomeMultidata, getHomeGoods} from "@/network/home.js"
import HomeRecommendView from '@/views/home/childComps/HomeRecommendView'
import FeatureView from '@/views/home/childComps/FeatureView'

import TabControl from '@/components/content/tabControl/TabControl'
import GoodsList from '@/components/content/Goods/GoodsList'
import Scroll from '@/components/common/scroll/Scroll'

export default {
  name: 'Home',
  components: {
    HomeRecommendView,
    FeatureView,
    TabControl,
    GoodsList,
    Scroll
  },
  data() {
    return {
      timeMsg: "",
      banners: [],
      recommends: [],
      goods: {
        pop: {page: 0, list: []},
        new: {page: 0, list: []},
        sell: {page: 0, list: []}
      },
      currentType: 'pop'
    }
  },
  created() {
    //请求多个数据
    this.homeMultidata()
    //请求商品数据
    this.homeGoodsdata('pop')
    this.homeGoodsdata('new')
    this.homeGoodsdata('sell')
  
  },
  methods: {
    /**
     * 事件监听相关方法
     */
    tabClick(index){
      switch (index) {
        case 0: 
        this.currentType = 'pop'
        break
        case 1: 
        this.currentType = 'new'
        break
        case 2: 
        this.currentType = 'sell'
      }
    },
    /**
     * 网络请求相关方法
     */
    homeMultidata() {
      getHomeMultidata().then(res => {
      this.banners = res.data.banner.list;
      this.recommends = res.data.recommend.list;
      })
    },
    homeGoodsdata(type) {
      const page = this.goods[type].page + 1;
      getHomeGoods(type, page).then(res => {
      this.goods[type].list.push(...res.data.list);
      this.goods[type].page += 1

      })
    }
  },
  computed: {
      
  },
  mounted() {
    
  //   const _this = this;
  //   _this.timer = setInterval(() => {
  //   let curTime = new Date();
  //   let year = curTime.getFullYear() <= 9 ? '0' + curTime.getFullYear() : curTime.getFullYear();
  //   let month = (curTime.getMonth() + 1) <= 9 ? '0' + (curTime.getMonth() + 1) : curTime.getMonth() + 1;
  //   let day = curTime.getDate() <= 9 ? '0' + curTime.getDate() : curTime.getDate();
  //   return _this.timeMsg = `${year}-${month}-${day}`;
  // },1000)
  // },
  // beforeDestroy: function() {
  //   //实例销毁前青出于定时器
  //   if (this.timer) {
  //     clearInterval(this.timer);
  //   }
  }

  
}
</script>

<style scoped>
  #home {
    position: relative;
    /* margin-top: 46px; */
    height: 100vh;
  }
  .van-nav-bar__title {
    color: #fff;
    font-size: 18px;
  }
  .van-hairline--bottom::after {
    border-bottom-width: 0px;
  }
  .home-nav-bar {
    background-color: rgb(228, 157, 193);
  }
  .img-swipe {
    width: 100%;
    height: 187.188px;
  }


  .a {
    height: 300px;
  }

  .tab-control {
    /* position: sticky; */
    top: 46px;
    z-index: 3;
  }
  .content {
    position: absolute;
    top: 46px;
    bottom: 49px;
    left: 0;
    right: 0;
    /* height: calc(100% - 95px); */
    overflow: hidden;
    /* margin-top: 473px; */
  }
</style>
