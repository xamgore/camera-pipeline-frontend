<template>
  <div id="app">

    <div class="description">
    <h1 style="margin: 0; margin-bottom: 0.3rem; font-family: Comfortaa">Склейка</h1>
      Ниже находятся фрагменты видео, снятые камерой.
      Выделите из них те, что вы хотите соединить и отправить на youtube.
    </div>

    <!--<div v-for="(d, day) in schedule">-->
      <!--<div v-for="l in d">-->
        <!--{{ k(l.time) }}-->
      <!--</div>-->
    <!--</div>-->

    <div v-for="m in parts">
      <movie :file="m.file" :date="m.date" :duration="m.duration"/>
    </div>

    <div class="floating">
      <div class="button">
      готово

      </div>
    </div>

  </div>
</template>

<script>
import Movie from './Movie.vue'

export default {
  name: 'app',
  components: {Movie},
  methods: {
    k(time) {
      let hour, minute = time.split(':')
      return moment({hour, minute}).format()
    }
  },
  data: () => ({
    parts: [
      {file:'00005.MTS', date: '2018-02-21 00:34:04+03:00', tdate: 'вчера в 12:57', duration: '00:47:06.000'},
      {file:'00000.MTS', date: '2018-02-22 14:34:04+03:00', tdate: 'вчера в 12:57', duration: '00:45:49.000'},
      {file:'00001.MTS', date: '2018-02-22 15:27:33+03:00', tdate: 'пт. 13:47', duration: '00:36:33.000'},
      {file:'00002.MTS', date: '2018-02-22 16:30:43+03:00', tdate: 'пт. 15:59', duration: '00:47:06.000'},
      {file:'00003.MTS', date: '2018-02-22 17:17:50+03:00', tdate: 'пт. 16:47', duration: '00:47:08.000'},
      {file:'00004.MTS', date: '2018-02-22 18:04:58+03:00', tdate: 'пт. 17:15', duration: '00:08:08.000'},
      {file:'00005.MTS', date: '2018-02-22 18:31:53+03:00', tdate: 'пт. 17:30', duration: '00:47:06.000'},
      {file:'00006.MTS', date: '2018-02-22 19:19:00+03:00', tdate: 'пт. 18:23', duration: '00:47:06.000'},
      ],


    schedule: {
      "Monday":   [
        {
          "time":  "10:00",
          "week":  "even",
          "type":  "practice",
          "title": "Формальные языки",
          "who":   "Вербицкая Е."
        }, {
          "time":  "12:00",
          "type":  "practice",
          "title": "Алгоритмы и структуры данных",
          "who":   "Слабодкин М.А."
        }, {
          "time":  "16:30",
          "week":  "odd",
          "type":  "lecture",
          "title": "Формальные языки",
          "who":   "Дворкин М.Э."
        }
      ],
      "Tuesday":  [
        {
          "time":  "10:00",
          "type":  "lecture",
          "title": "C++",
          "who":   "Лесин В.М."
        }, {
          "time":  "14:30",
          "type":  "lecture",
          "title": "Java",
          "who":   "Кузнецов А.м."
        }, {
          "time":  "16:30",
          "type":  "lecture",
          "title": "Машинное обучение",
          "who":   "Шпильман А."
        }
      ],
      "Thursday": [
        {
          "time":  "10:00",
          "type":  "lecture",
          "title": "Алгоритмы и структуры данных",
          "who":   "Смаль А.В."
        }, {
          "time":  "14:30",
          "type":  "lecture",
          "title": "Матлогика",
          "who":   "Москвин Д.Н."
        }, {
          "time":  "16:30",
          "week":  "even",
          "type":  "practice",
          "title": "Матлогика",
          "who":   "Москвин Д.Н"
        }, {
          "time":  "16:30",
          "week":  "odd",
          "type":  "lecture",
          "title": "Типы в языках программирования",
          "who":   "Москвин Д.Н"
        }, {
          "time":  "18:30",
          "type":  "practice",
          "title": "Типы в языках программирования",
          "who":   "Москвин Д.Н."
        }
      ],
      "Friday":   [
        {
          "time":  "10:00",
          "type":  "practice",
          "title": "Java",
          "who":   "Саввинов Д."
        }, {
          "time":  "12:00",
          "type":  "lecture",
          "title": "Software Design",
          "who":   "Брыксин Т."
        }, {
          "time":  "14:30",
          "type":  "practice",
          "title": "Software Design",
          "who":   "Литвинов Ю."
        }
      ]
    },
  })
}
</script>

<style>
html, body {
  padding: 0;
  margin: 0;
}

#app {
  /*font-family: 'Avenir', Helvetica, Arial, sans-serif;*/
  font-family: 'PT Sans', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  /*margin-top: 60px;*/
}

html {
  overflow: scroll;
  overflow-x: hidden;
}

::-webkit-scrollbar {
  width: 0;  /* remove scrollbar space */
  background: transparent;  /* optional: just make scrollbar invisible */
  display: none;
}

/* optional: show position indicator */
::-webkit-scrollbar-thumb {
  /*background: rgba(0, 0, 0, 0.14);*/
}

.description {
  margin-top: 0.5rem;
  margin-bottom: 2.5rem;
  padding: 1rem 1rem;
  padding-bottom: 0;
}


.floating {
  display: flex;
  justify-content: center;
  position: fixed;
  height: 100%;
  width: 100%;
}
  .button {
    background: red;
  }
</style>
