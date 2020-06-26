<template> 

  <div class="tabBarItem" @click="itemClick">   
    <!-- <img src="../../assets/img/tabbar/home.png" alt="">
    <div>首页</div> -->
    <div v-if="!isActive"><slot name="itemIcon"></slot></div>
    <div v-else><slot name="itemIconActive"></slot></div>
    <div :style="activeStyle"><slot name="itemText"></slot></div>
  </div>
</template>

<script>
    export default {
        name:"tabBarItem",
        props: {
          path: String,
          activeColor: {
            type: String,
            default: 'red'
          }
        },
        data() {
          return {
            // isActive: false
          }
        },
        computed: {
          isActive() {
            return this.$route.path.indexOf(this.path) !== -1
          },
          activeStyle() {
            return this.isActive ? {color: this.activeColor} : {}
          }
        },
        methods: {
          itemClick() {
            this.$router.push(this.path);
          }
        },
    }
</script>

<style>

  .tabBarItem {
    flex: 1;
    text-align: center;
    height: 49px;
    font-size: 12px;
  }
  .tabBarItem img {
    width: 24px;
    height: 24px;
    margin-top: 5px;
    
    vertical-align: middle;
    margin-bottom: 2px;
  }
</style>