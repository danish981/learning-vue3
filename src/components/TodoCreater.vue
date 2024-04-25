<script setup>
import { reactive, ref } from "vue"


// testing the how ref works, it will be string 
// const todo = ref("testing") ;

// testing how reactive works, it will be an object
const todoState = reactive({
    todo : 'testing input'
})


</script>


<template>
    <div class="input-wrap">
        <input type="text" v-model="todoState.todo">
        <button>Create</button>
    </div>

    <p>{{ todoState.todo }}</p>

</template>


<style lang="scss" scoped>
.input-wrap {
  display: flex;
  transition: 250ms ease;
  border: 2px solid #41b080;

  &:focus-within {
    box-shadow: 0 -4px 6px -1px rgb(0 0 0 / 0.1),
      0 -2px 4px -2px rgb(0 0 0 / 0.1);
  }

  input {
    width: 100%;
    padding: 8px 6px;
    border: none;

    &:focus {
      outline: none;
    }
  }

  button {
    padding: 8px 16px;
    border: none;
  }
}
</style>