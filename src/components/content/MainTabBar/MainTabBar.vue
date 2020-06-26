<template>
  <tab-bar>
    <tab-bar-item path="/home" activeColor="rgb(228, 157, 193)">
      <img slot="itemIcon" src="@/assets/img/tabbar/home.png" alt="">
      <img slot="itemIconActive" src="@/assets/img/tabbar/home-active.png" alt="">
      <div slot="itemText">首页</div>
    </tab-bar-item>
    <tab-bar-item path="/category" activeColor=" rgb(228, 157, 193)">
      <img slot="itemIcon" src="@/assets/img/tabbar/category.png" alt="">
      <img slot="itemIconActive" src="@/assets/img/tabbar/category-active.png" alt="">
      <div slot="itemText">分类</div>
    </tab-bar-item>
    <tab-bar-item path="/shopcart" activeColor=" rgb(228, 157, 193)">
      <img slot="itemIcon" src="@/assets/img/tabbar/shopcart.png" alt="">
      <img slot="itemIconActive" src="@/assets/img/tabbar/shopcart-active.png" alt="">
      <div slot="itemText">购物车</div>
    </tab-bar-item>
    <tab-bar-item path="/profile" activeColor=" rgb(228, 157, 193)">
      <img slot="itemIcon" src="@/assets/img/tabbar/profile.png" alt="">
      <img slot="itemIconActive" src="@/assets/img/tabbar/profile-active.png" alt="">
      <div slot="itemText">我的</div>
    </tab-bar-item>
  </tab-bar>
</template>

<script>
  import tabBar from '@/components/common/tabBar/tabBar.vue'
  import tabBarItem from '@/components/common/tabBar/tabBarItem.vue'
export default {
  name: 'mainTabBar',
  
  data(){
    return {}
  },
  components: {
    tabBar,
    tabBarItem
  },
  created(){},
  mounted(){},
  methods: {}
}
</script>

<style lang='scss' scoped>

</style>
