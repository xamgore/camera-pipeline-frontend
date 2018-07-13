<template>
  <div>
    <transition-group name="list-complete" tag="div">
      <radio-button
        v-for="i in items"
        :key="i"
        v-text="i"
        class="list-complete-item"
        :active="i === value"
        @click="$emit('input', i)"
      />
    </transition-group>
  </div>
</template>


<script>
import RadioButton from '@/components/RadioButton.vue'

export default {
  name: 'radio-list',
  components: { RadioButton },
  props: {
    value: String,
    items: {},
  }
}
</script>


<style>

.list-complete-item {
  transition: transform .4s;
}

.list-complete-enter, .list-complete-leave-to {
  opacity: 0;
  transform: translateX(-30px);
}

.list-complete-leave-active {
  position: absolute;
}

</style>
