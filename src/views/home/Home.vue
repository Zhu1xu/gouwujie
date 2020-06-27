<template>
<div id="home">
  <van-Nav-bar title = "购物街" class = "home-nav-bar" fixed/>

  <van-swipe :autoplay="3000">
  <van-swipe-item v-for="(image, index) in banners" :key="index">
    <img v-lazy="image.image" class="img-swipe"/>
  </van-swipe-item>
  </van-swipe>
  <home-recommend-view :recommends="recommends"></home-recommend-view>
  <feature-view></feature-view>
  <tab-control :titles="['流行', '新款', '精选']"></tab-control>
  <!-- <p>{{timeMsg}}</p> -->
  <div class="a"></div>
  
</div>


</template>

<script>
import {getHomeMultidata} from "@/network/home.js"
import HomeRecommendView from '@/views/home/childComps/HomeRecommendView'
import FeatureView from '@/views/home/childComps/FeatureView'

import TabControl from '@/components/content/tabControl/TabControl'

export default {
  name: 'Home',
  components: {
    HomeRecommendView,
    FeatureView,
    TabControl,
  },
  data() {
    return {
      timeMsg: "",
      banners: [],
      recommends: [],

    }
  },
  created() {
    //请求多个数据
    getHomeMultidata().then(res => {
      this.banners = res.data.banner.list;
      this.recommends = res.data.recommend.list;
    })
  },
  computed: {
      
  },
   methods: {
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

<style>
  #home {
    padding-top: 46px;
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
</style>
