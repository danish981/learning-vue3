<script setup>
import TodoCreater from "@/components/TodoCreater.vue";
import { ref } from "vue";
import { uid } from "uid"; // to make the ids unique for each todo item
import TodoItem from "@/components/TodoItem.vue";

const todoList = ref([]);

const createTodo = (todo) => {
  todoList.value.push({
    id: uid(),
    todo, // the field and the property are the same, so we can just use one
    isCompleted: null,
    isEditing: null,
  });
};
</script>

<template>
  <main>
    <h1>Todos application</h1>

    <!-- we are taking the value from the component that was emitted from the TodoCreater and passing it to the createTodo function -->
    <TodoCreater @create-todo="createTodo" />
    <ul class="todo-list">
      <TodoItem v-for="todo in todoList" :key="todo.id" :todo="todo" />
    </ul>
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
}
</style>

