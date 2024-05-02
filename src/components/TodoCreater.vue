<script setup>
import { ref, defineEmits, reactive } from "vue";
import TodoButton from "./TodoButton.vue";

const emit = defineEmits(["create-todo"]);

const todoState = reactive({
  todo: "", // the todo string, which is the value of the input
  invalid: null,  // will be true if the input value is empty
  errorMsg: null, // will be true if the input value is empty
});

const createTodo = () => {

  // in DOM, we can access the reactive value by directly writing the variable name, but in script we need to use .value

  todoState.invalid = null; // can say NULL or false, but i have not checked it with false value
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

  <div class="input-wrap" :class="{ 'input-err' : todoState.invalid }">
    <input type="text" v-model="todoState.todo" />
    <TodoButton @click="createTodo" />
  </div>

  <!-- ? both the v-if and v-show work the same but here are the differences -->

  <!-- will not render the element to the DOM -->
  <!-- <p class="errorMsg" v-if="todoState.invalid">{{ todoState.errorMsg }}</p> -->
  
  <!-- will render the element to the DOM but make it invisible by display: none -->
  <!-- we are gonna usen the v-show because the we are gonna click the create button multiple times -->
  <!-- it will just hide-n-show the element from the DOM  -->
  
  <p class="errorMsg" v-show="todoState.invalid">{{  todoState.errorMsg }}</p>

  
</template>


<style lang="scss" scoped>
.input-wrap {
  display: flex;
  transition: 250ms ease;
  border: 2px solid #41b080;


  &.input-err {
    border-color: #ff0000;
  }

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


.errorMsg {
  margin-top: 6px;
  font-size : 12px;
  text-align: center;
  color : red;
}

</style>