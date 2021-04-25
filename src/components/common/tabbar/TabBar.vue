<template>
  <div>
    <div id="tab-bar">
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  name:'TabBar'
}
</script>

<style>

  #tab-bar{
    display: flex;

    position:fixed;
    left: 0px;
    right: 0px;
    bottom: 0px;

    background-color: #f6f6f6;

    box-shadow: 0 -2px 1px rgba(100,100,100,0.1);
  }
</style>
