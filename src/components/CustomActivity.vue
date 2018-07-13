<template>
  <form v-on:submit.prevent="kek">
    <div class="field">
      <label>название</label>
      <input type="text" v-model="title" placeholder="Кузя — отзывы" required/>
    </div>

    <div class="field">
      <label>описание на youtube</label>
      <textarea v-model="description" rows="5"
                :placeholder='["Кузя объясняет, как нужно заполнять опрос с отзывами, чтобы преподы",
                                     "не стали использовать плохие слова в отношении студентов."].join(" ")'/>
    </div>

    <div class="field">
      <checkbox v-model="normalizeSound">нормализовать звук</checkbox>
    </div>

    <input type="submit" value="готово"/>
  </form>
</template>


<script>
import Checkbox from './Checkbox.vue'

export default {
  name: 'custom-activity',
  components: { Checkbox },
  data: () => ({
    title: '',
    description: '',
    normalizeSound: true,
  }),
  methods: {
    kek() {
      window.console.log('kek')
    }
  }
}
</script>

<style>
</style>
