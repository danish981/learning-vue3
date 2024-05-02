<script setup>
import { ref, defineEmits, reactive } from "vue";

const emit = defineEmits(["create-todo"]);

const todoState = reactive({
  todo: "", // the todo string, which is the value of the input
  invalid: null,  // will be true if the input value is empty
  errorMsg: null, // will be true if the input value is empty
});

const createTodo = () => {

  // in DOM, we can access the reactive value by directly writing the variable name, but in script we need to use .value

  todoState.invalid = null;
  if (todoState.todo !== "") {
    emit("create-todo", todoState.todo);
    todoState.todo = "";
    return;
  }

  todoState.invalid = true;
  todoState.errorMsg = 'Todo Value cannot be empty'
};
</script>


<template>

  <div class="input-wrap">
    <input type="text" v-model="todoState.todo" />
    <button @click="createTodo">Create</button>
  </div>

  <!-- ? both the v-if and v-show work the same but here are the differences -->

  <!-- will not render the element to the DOM -->
  <p class="errorMsg" v-if="todoState.invalid">{{ todoState.errorMsg }}</p>
  
  <!-- will render the element to the DOM but make it invisible by display: none -->
  <!-- <p class="errorMsg" v-show="todoState.invalid">{{  todoState.errorMsg }}</p> -->

  
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