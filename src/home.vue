<template>
<div id="home">
  <component :is="currentPage"></component>
</div>
</template>

<script>
import Vue from 'vue'
import App1 from './components/App1.vue'
import Menu from './components/menu.vue'
import dataInput from './components/dataInput.vue'
Vue.component('dataInput', dataInput)
Vue.component('App1', App1)
Vue.component('Menu', Menu)
export default {
  name: 'home',
  data: function() {
    return {
      currentPage: null,
      userName: 'null',
      gender: 'null',
      age: null,
      already: null,
      levels: [],
      nums: [],
      current: 0,
      total: 10,
    }
  },
  mounted: function(){
    let that = this
    console.log('home mounted')
    for(let i = 0; i < that.total; i++){
      console.log(i)
      if(i < 6){
        that.levels.push('high/')
        that.nums.push(i)
      } else {
        that.levels.push('low/')
        that.nums.push(i - 6)
      }
    }
    for(let j = that.nums.length - 1; j > 0; j--){
      let r = Math.floor(Math.random() * (j + 1));
      let tmp = that.nums[j];
      that.nums[j] = that.nums[r];
      that.nums[r] = tmp;
      tmp = that.levels[j];
      that.levels[j] = that.levels[r];
      that.levels[r] = tmp;
    }
    console.log(that.levels)
    that.currentPage = 'dataInput'
  }
}
</script>
