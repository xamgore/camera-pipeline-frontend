<template>
  <span class="choice" :class="{ active }" @click="$emit('click', $event)">
    <slot></slot>
  </span>
</template>

<script>
  export default {
    name: "Button",
    props: {active: Boolean},
    methods: {
      chooseLesson(e) {
        console.log(e);
      }
    }
  }
</script>

<style scoped>
.choice {
  font-weight: bold;
  color: #2196F3;
  background: white;
  border: 1.2px solid #2196F3;
  border-radius: 20px;
  padding: 0 0.5em 0.1em;
  margin-right: 0.5em;
  margin-bottom: 0.3em;
  font-size: 0.85em;
  white-space: nowrap;
  display: inline-block;
  transition: all .4s;
}

.choice.active {
  color: white;
  background: #2196F3;
}
</style>
