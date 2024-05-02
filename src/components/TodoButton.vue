<script setup>
</script>


<!-- slots are used to make our content more and more dynamic by passing the content from parent component to child component -->

<template>
  <button>
    <!-- we can use the slot to add content to the button -->
    <!-- if we have multiple slots we can name them, but this fallback slot will be used if there is no named slot -->
    <slot>create</slot>
  </button>
</template>


<style lang="scss" scoped>

button {
  padding: 8px 16px;
  border: none;
}
</style>