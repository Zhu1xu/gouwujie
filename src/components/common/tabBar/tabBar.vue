<template>
    <div id="tabBar">
        <slot></slot>
    </div>

</template>

<script>
  export default {
    name:"tabBar"
  }
</script>

<style>
 #tabBar {
    display: flex;
    position: fixed;
    height: 49px;
    left: -1px;
    bottom: -2px;
    right: 0;
    box-shadow: 0 3px 10px rgba(100, 100, 100, .2);
    background-color: #f6f6f6;
  }


</style>