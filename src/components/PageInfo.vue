<template>
  <div>

    <description title="Склейка" style="margin-bottom: 2rem">
      Заполни данные, чтобы мы обновили их на youtube:
    </description>


    <div style="padding: 0 1rem 1rem">
      <div class="field">
        <label>тип</label>
        <radio-list v-model="category" :items="['лекция', 'практика', 'прочее']" style="margin-top: 0.2em"/>
      </div>

      <transition name="fade" mode="out-in" :duration="300">
        <custom-activity v-if="category === 'прочее'" key="other"/>

        <study-activity v-else-if="isStudyActivity" key="study" :subjects="subjects" :category="category"/>
      </transition>
    </div>

  </div>
</template>

<script>
import Description from './Description'
import RadioList from './RadioList'
import StudyActivity from './StudyActivity'
import CustomActivity from './CustomActivity'

export default {
  name: 'page-info',
  props: ['subjects'],
  components: { CustomActivity, StudyActivity, RadioList, Description },
  data: () => ({
    category: null,
  }),
  computed: {
    isStudyActivity() {
      return ['лекция', 'практика'].includes(this.category)
    }
  }
}
</script>

<style>
.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}

.fade-enter, .fade-leave-to {
  opacity: 0;
}
</style>
