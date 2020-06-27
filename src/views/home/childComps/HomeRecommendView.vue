<template>
  <div class="recommend">
    <div v-for="item in recommends" class="recommend-item">
      <a :href="item.link">
        <img :src="item.image" alt="">
        <div>{{item.title}}</div>
      </a>
    </div>
  </div>
</template>
<script>
export default {
  name: "HomeRecommendView",
  props: {
    recommends: {
      type: Array,
      default() {
          return []
      }
    }
  }
}
</script>
<style scoped>
  .recommend {
    display: flex;
    text-align: center;
    font-size: 12px;
    padding: 10px 0 10px;
    border-bottom: 20px solid rgb(245, 227, 233);
  }
  .recommend-item {
    flex: 1;
  }
  img {
      width: 90%;
      margin-bottom: 8px;
  }
</style>