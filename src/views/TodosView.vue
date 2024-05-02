<script setup>
import TodoCreater from "@/components/TodoCreater.vue";

import { Icon } from "@iconify/vue";
import { ref } from "vue";
import { uid } from "uid"; // to make the ids unique for each todo item
import TodoItem from "@/components/TodoItem.vue";

const todoList = ref([]);

const fetchTodoListFromLocalStorage = () => {
  const storedTodoList = localStorage.getItem("todoList");
  if (storedTodoList) {
    todoList.value = JSON.parse(storedTodoList);
  }
};

// everytime on the page laods, this function will be called and it will fetch the todo list
fetchTodoListFromLocalStorage();

const setTodoListToLocalStorage = () => {
  localStorage.setItem("todoList", JSON.stringify(todoList.value));
};

const createTodo = (todo) => {
  todoList.value.push({
    id: uid(),
    todo, // the field and the property are the same, so we can just use one
    isCompleted: null,
    isEditing: null,
  });

  setTodoListToLocalStorage();
};

const toggleTodoComplete = (index) => {
  // index is the todo position
  todoList.value[index].isCompleted = !todoList.value[index].isCompleted;
  setTodoListToLocalStorage();
};

const toggleEditTodo = (index) => {
  todoList.value[index].isEditing = !todoList.value[index].isEditing;
  setTodoListToLocalStorage();
};

const updateTodo = (updatedTodoValue, index) => {
  todoList.value[index].todo = updatedTodoValue;
  setTodoListToLocalStorage();
};

const deleteTodo = (index) => {
  todoList.value = todoList.value.filter((todo) => todo.id !== index);
  setTodoListToLocalStorage();
};
</script>

<template>
  <main>
    <h1>Todos application</h1>

    <!-- we are taking the value from the component that was emitted from the TodoCreater and passing it to the createTodo function -->
    <TodoCreater @create-todo="createTodo" />

    <!-- the todo list stacked items added into the reactive element array -->
    <ul class="todo-list" v-if="todoList.length > 0">
      <!-- ! vscode vue extension is showing the error that custom elements in iteration require 'v-bind:key' directive -->
      <!-- ! so for that same purpose, we are using the index which is the key that is being passed to the TodoItem component -->
      <TodoItem
        v-for="(todo, index) in todoList"
        v-bind:key="todo.id"
        :index="index"
        :todo="todo"
        @toggle-complete="toggleTodoComplete"
        @edit-todo="toggleEditTodo"
        @update-todo="updateTodo"
        @delete-todo="deleteTodo"
      />
    </ul>

    <!-- the message being displayed if there is no todo item in the todo list -->
    <div class="todos-msg" v-else>
      <Icon icon="noto-v1:sad-but-relieved-face" width="22" />
      <span>You have no todo's to complete !! Add one!</span>
    </div>
  </main>
</template>

<style lang="scss" scoped>
main {
  display: flex;
  flex-direction: column;
  max-width: 500px;
  width: 100%;
  margin: 0 auto;
  padding: 40px 16px;
  h1 {
    margin-bottom: 16px;
    text-align: center;
  }

  .todo-list {
    display: flex;
    flex-direction: column;
    list-style: none;
    margin-top: 24px;
    gap: 20px;
  }

  .todos-msg {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 8px;
    margin-top: 24px;
  }
}
</style>

