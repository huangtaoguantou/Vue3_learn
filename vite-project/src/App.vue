<script setup>
import { defineStore } from 'pinia';
// useMain  可以是 useUser、useCart 之类的名字
// defineStore('main',{..}) 在devtools 就使用 main 这个名
const useMain = defineStore('main', {
  // 相当于data
  state: () => {
    return {
      // 所有这些属性都将自动推断其类型,如果推断失败可以试下 as xxx
      counter: 0,
      name: 'Eduardo',
    };
  },
  // 相当于计算属性
  getters: {
    doubleCount: state => {
      return state.counter * 2;
    },
  },
  // 相当于vuex的 mutation + action，可以同时写同步和异步的代码
  actions: {
    increment() {
      this.counter++;
    },
    randomizeCounter() {
      setTimeout(() => {
        this.counter = Math.round(100 * Math.random());
      }, 0);
    },
  },
});
</script>

<template>
  <router-view></router-view>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
