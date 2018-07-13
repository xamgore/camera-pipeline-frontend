<template>
  <div>
    <description title="Склейка">
      Ниже находятся фрагменты видео, снятые камерой.
      Выделите из них те, что вы хотите соединить и отправить на youtube.
    </description>

    <div v-for="m in movies">
      <movie :file="m.file" :date="m.date" :duration="m.duration" v-model="m.chosen"/>
    </div>

    <transition name="up-down">
      <div class="floating" v-show="hasOneOrMoreSelectedItems">
        <button class="submit" @click="$emit('ready')">готово</button>
      </div>
    </transition>

  </div>
</template>

<script>
import Movie from './Movie.vue'
import Description from './Description.vue'

export default {
  name: 'page-concat',
  props: ['movies'],
  components: { Movie, Description },
  computed: {
    hasOneOrMoreSelectedItems() {
      return this.movies.some(m => m.chosen)
    }
  }
}
</script>

<style>
.floating {
  display: flex;
  justify-content: center;
  position: fixed;
  bottom: 0;
  width: 100%;
  transition: transform .3s;
}

.floating button {
  border-radius: 0;
  height: 2.5rem;
  outline: 0;
}

.floating.up-down-enter, .floating.up-down-leave-to {
  transform: translateY(40px);
}
</style>
