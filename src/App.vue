<script setup>
import { RouterView } from "vue-router";
import TodoHeader from "./components/TodoHeader.vue";
</script>

<template>
  <TodoHeader />
  <RouterView />
</template>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Rubik:ital,wght@0,300..900;1,300..900&display=swap");

/* if you define the fallback font, it will be used if the browser doesn't support the font, but in this case it is not working, if we define sans-serif , it wont be working */
* {
  font-family: "Rubik";
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.container {
  max-width: 1100px;
  margin: 0 auto;
}
</style>