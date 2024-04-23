<script setup>
import { RouterView } from 'vue-router'
import TodoHeaver from './components/TodoHeaver.vue';

</script>

<template>
  <TodoHeaver />
  <RouterView />
</template>


<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Rubik:ital,wght@0,300..900;1,300..900&display=swap');


* {
  font-family: "Rubik, sans-serif";
  margin : 0;
  padding: 0;
  box-sizing: border-box;
}

.container {
  max-width: 1100px;
  margin: 0 auto;
}



</style>