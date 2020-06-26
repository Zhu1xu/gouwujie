<template>
<div>
  <van-Nav-bar title = "购物街" class = "home-nav-bar"/>
  <p>首页</p>
  <img src="@/assets/img/mmexport1593172955122.jpg" alt="">
  <p>{{timeMsg}}</p>
</div>

</template>

<script>
import {getHomeMultidata} from "@/network/home.js"
export default {

  name: 'Home',
  data() {
    return {
      timeMsg: "",
      banners: [],
      recommends: []
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
    onClickLeft() {
      Toast('返回');
    },
    onClickRight() {
      Toast('按钮');
    },
  },
  mounted() {
    
    const _this = this;
    _this.timer = setInterval(() => {
    let curTime = new Date();
    let year = curTime.getFullYear() <= 9 ? '0' + curTime.getFullYear() : curTime.getFullYear();
    let month = (curTime.getMonth() + 1) <= 9 ? '0' + (curTime.getMonth() + 1) : curTime.getMonth() + 1;
    let day = curTime.getDate() <= 9 ? '0' + curTime.getDate() : curTime.getDate();
    return _this.timeMsg = `${year}-${month}-${day}`;
  },1000)
  },
  beforeDestroy: function() {
    //实例销毁前青出于定时器
    if (this.timer) {
      clearInterval(this.timer);
    }
  }

  
}
</script>

<style>
  .van-nav-bar__title {
    color: #fff;
    font-size: 18px;
  }
  .home-nav-bar {
    font-size: 18px;
    background-color: rgb(228, 157, 193);
  }
</style>
