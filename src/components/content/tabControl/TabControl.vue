<template>
  <div class="tab-control">
    <div class="tab-control-item" 
    v-for="(item,index) in titles" :key="index"
    :class="{active:index===currentIndex}"
    @click="itemClick(index)">
      <span>{{item}}</span>
    </div>
  </div>
</template>

<script>
export default {
  name:'TabControll',
  props:{
    titles:{
      type:Array,
      default(){
        return []
      }
    }
  },
  data(){
    return {
      currentIndex:0
    }
  },
  methods:{
    itemClick(index){
      this.currentIndex=index
    }
  }
}
</script>

<style>
  .tab-control{
    display: flex;
    text-align: center;
    font-size: 15px;
    height: 40px;
    line-height: 40px;
  }
  .tab-control-item{
    flex:1;
  }
  .active span{
    padding: 3px;
    border-bottom: 3px solid var(--color-tint);
  }
  .active{
    color: var(--color-high-text);
  }
</style>