<template>
  <div class="tab-control">
    <div v-for="(item, index) in titles" class="tab-item" 
      :class="{active: index === currentIndex}"
      @click="tabClick(index)">
      <span>{{item}}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "TabControl",
  props: {
    titles: {
      type: Array,
      default() {
        return []
      }
    }
  },
  data() {
    return {
      currentIndex: 0
    }
  },
  methods: {
    tabClick(index) {
      this.currentIndex = index;
      this.$emit('tabClick', index)
    }
  }
}
</script>

<style scoped>
  .tab-control {
    display: flex;
    font-size: 17px;
    height: 40px;
    line-height: 40px;
    color: #555;
    text-align: center;
    background-color: #fff;
  }
  .tab-item {
    flex: 1;

  }
  .tab-item span {
    padding: 5px;
  }
  .active {
    color: rgb(228, 157, 193);
    
  }
  .active span {
    border-bottom: solid 3px rgb(228, 157, 193);
  }
</style>