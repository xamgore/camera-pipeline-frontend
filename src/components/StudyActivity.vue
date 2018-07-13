<template>
  <form v-on:submit.prevent="kek">
    <div class="field">
      <label>предмет</label>
      <radio-list v-model="subjectName" :items="subjectNames" style="margin-top: 0.2em"/>
    </div>

    <transition name="fade">
      <div v-show="chosenSubject">
        <div class="field">
          <label>тема лекции</label>
          <input v-model="title" type="text" placeholder="UML-диаграммы" required>
        </div>

        <div class="field">
          <label>описание на youtube</label>
          <textarea v-model="description"
                    placeholder="Изучаем 20 видов диаграмм и молим бога, что нам не придётся их рисовать"/>
        </div>

        <div class="field">
          <checkbox v-model="normalizeSound">нормализовать звук</checkbox>
        </div>

        <div class="field">
          <checkbox v-model="parseSlides" disabled>искать слайды на видео</checkbox>
        </div>

        <input type="submit" value="готово"/>
      </div>
    </transition>
  </form>
</template>


<script>
import Checkbox from './Checkbox.vue'
import RadioList from './RadioList'

export default {
  name: 'study-activity',
  components: { Checkbox, RadioList },
  props: ['subjects', 'category'],
  data: () => ({
    title: '',
    description: '',
    normalizeSound: true,
    parseSlides: false,
    subjectName: null,
  }),
  computed: {
    subjectNames() {
      return this.subjects.filter(s => s.category === this.category).map(s => s.title)
    },
    chosenSubject() {
      let candidates = this.subjects.filter(s => s.category === this.category && s.title === this.subjectName)
      return candidates.length ? candidates[0] : null
    }
  },
  methods: {
    kek() {
      window.console.log('kek')
    }
  }
}
</script>


<style>
</style>
