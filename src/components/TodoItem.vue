<script setup>
import { Icon } from "@iconify/vue";

// props are defined the parameter could be array and object,
// but the array wont give you the details what the props are
// but the object will give you the details

// in this case, we are using the todo object
const props = defineProps({
  // defineProps macro
  todo: {
    type: Object,
    required: true,
    // we can also define the default value for the props
  },
  index: {
    type: Number,
    required: true,
  },
});


// defined emits that this data will be passed from child component to parent component
defineEmits(["toggle-complete", 'edit-todo', 'update-todo']);

</script>


<template>
  <li>

    <!-- the checkbox to see if a particular todo item is completed or not -->
    <input type="checkbox" :checked="todo.isCompleted" @input="$emit('toggle-complete', index)" />


    <!-- looping through each todo item from the parent component -->
    <div class="todo">
      <input type="text" v-if="todo.isEditing" :value="todo.todo" @input="$emit('update-todo', $event.target.value, index )" />

      <!-- we are going to add a strike-through to this span element if the todo item is completed -->
      <span v-else :class="{ 'completed-todo': todo.isCompleted }">
        {{ todo.todo }}
      </span>
    </div>


    <!-- the actions buttons for each todo item -->
    <div class="todo-actions">
      <Icon
        v-if="todo.isEditing"
        icon="ph:check-circle"
        class="icon"
        color="#41b080"
        width="22"
        @click="$emit('edit-todo', index)"
      />
      <Icon
        v-else
        icon="ph:pencil-fill"
        class="icon"
        color="#41b080"
        width="22"
        @click="$emit('edit-todo', index)"
      />
      <Icon icon="ph:trash" class="icon" color="#f95e5e" width="22" />
    </div>

  </li>
</template>


<style lang="scss" scoped>
li {
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 16px 10px;
  background-color: #f1f1f1;
  box-shadow: 0 20px 25px -5px rgb(0 0 0 / 0.1),
    0 8px 10px -6px rgb(0 0 0 / 0.1);

  &:hover {
    .todo-actions {
      opacity: 1;
    }
  }

  .completed-todo {
    text-decoration: line-through;
  }

  input[type="checkbox"] {
    appearance: none;
    width: 20px;
    height: 20px;
    background-color: #fff;
    border-radius: 50%;
    box-shadow: 0 4px 6px -1px rgb(0 0 0 / 0.1), 0 2px 4px -2px rgb(0 0 0 / 0.1);

    &:checked {
      background-color: #41b080;
    }
  }

  .todo {
    flex: 1;

    input[type="text"] {
      width: 100%;
      padding: 2px 6px;
      border: 2px solid #41b080;
    }
  }

  .todo-actions {
    display: flex;
    gap: 6px;
    opacity: 0;
    transition: 150ms ease-in-out;
    .icon {
      cursor: pointer;
    }
  }
}
</style>