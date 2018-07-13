<template>
  <div class="description">
    <h1>{{ title }}</h1>
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: "Description",
  props: ['title'],
}
</script>

<style scoped>
.description {
  margin-top: 0.5rem;
  margin-bottom: 2.5rem;
  padding: 1rem 1rem;
  padding-bottom: 0;
}

h1 {
  margin: 0;
  margin-bottom: 0.3rem;
  font-family: Comfortaa, sans-serif;
}
</style>
