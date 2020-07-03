<template>
  <div class="list-item">
    <img :src="goodsItem.show.img" alt="" @load="imageload">
    <div class="good-info">
      <p>{{goodsItem.title}}</p>
      <span class="price">{{goodsItem.price}}</span>
      <span class="collect">{{goodsItem.cfav}}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "GoodsListItem",
  props: {
    goodsItem: {
      type: Object,
      default() {
        return {}
      }
    }
  },
  methods: {
    imageload() {
      
    }
  }
}
</script>

<style scoped>
  .list-item {
    padding-bottom: 40px;
    position: relative;
    width: 45%;
  }
  .list-item img {
    width: 100%;
    border-radius: 5px;
  }
  .good-info {
    font-size: 12px;
    position: absolute;
    bottom: 5px;
    left: 0;
    right: 0;
    overflow: hidden;
    text-align: center;
  }
  .good-info p {
    color: #666;
    text-overflow: ellipsis;
    white-space: nowrap;
    overflow: hidden;
    margin-bottom: 3px;
  }
</style>