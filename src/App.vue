<template>
  <div id="app">

    <div class="description">
      <h1 style="margin: 0; margin-bottom: 0.3rem; font-family: Comfortaa">Склейка</h1>
      <div style="margin-bottom: 2rem">Заполни данные, чтобы мы обновили их на youtube:</div>

      <label>тип</label>
      <div style="margin-top: 0.2em;">
        <span class="choice chosen">лекция</span>
        <span class="choice">практика</span>
        <span class="choice">прочее</span>
      </div>

      <div class="field">
        <label>предмет</label>
        <div style="margin-top: 0.2em">
          <span v-for="subj in subjects" v-text="subj"
                class="choice" :class="{chosen: subj === 'Software Design'}"></span>
        </div>
      </div>

      <div class="field">
        <label>тема лекции</label>
        <input type="text" name="title" placeholder="UML-диаграммы">
      </div>

      <div class="field">
        <label>описание на youtube</label>
        <textarea name="title" placeholder="UML-диаграммы"></textarea>
      </div>

      <div class="field" style="flex-direction: row;">
        <input type="checkbox" id="normalize-sound" checked/>
        <label for="normalize-sound" style="width:100%">нормализовать звук</label>
      </div>

      <br>
      <button class="submit">готово</button>

    </div>


  </div>
</template>

<script>
import Movie from './components/Movie.vue'

export default {
  name: 'app',
  components: {Movie},
  computed: {
    subjects() {
      let titles = Array.prototype.concat(...Object.values(this.schedule))
      return Array.from(new Set(titles.map(subj => subj.title))).sort((a, b) => a.length - b.length)
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

    schedule: {},
  }),

  created() {
    fetch('/schedule.json')
      .then(res => res.json())
      .then(res => {this.schedule = res})
  }
}
</script>

<style>
html, body {
  box-sizing: border-box;
  padding: 0;
  margin: 0;
}

* {box-sizing: inherit;}

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
}

.choice.chosen {
  color: white;
  background: #2196F3;
}


.field {
  display: flex;
  margin: 1.3rem 0;
  flex-direction: column;
}

textarea, input[type=text], input[type=date], input[type=number], input[type=email], select {
  width: 100%;
  height: 1.8em;
  line-height: 1.8em;
  margin: 0.2em 0;
  padding-left: 0.5em;
  border: 1.3px solid #2196F3;
  border-radius: 3px;
}

textarea {
  height: inherit;
}

input[type=text]:disabled {
  border-color: #9E9E9E;
}

label {
  font-weight: bold;
}

button.submit {
  /*all: initial;*/
  background: #2196F3;
  color: white;
  border: 0;
  border-radius: 2px;
  height: 2rem;
  width: 100%;
  font: inherit;
  font-weight: 700;
}



/* Base for label styling */
[type="checkbox"]:not(:checked),
[type="checkbox"]:checked {
  position: absolute;
  left: -9999px;
}
[type="checkbox"]:not(:checked) + label,
[type="checkbox"]:checked + label {
  position: relative;
  padding-left: 1.95em;
  cursor: pointer;
}

/* checkbox aspect */
[type="checkbox"]:not(:checked) + label:before,
[type="checkbox"]:checked + label:before {
  content: '';
  position: absolute;
  left: 0; top: 0;
  width: 1.25em; height: 1.25em;
  border: 2px solid #ccc;
  background: #fff;
  border-radius: 4px;
  box-shadow: inset 0 1px 3px rgba(0,0,0,.1);
}
/* checked mark aspect */
[type="checkbox"]:not(:checked) + label:after,
[type="checkbox"]:checked + label:after {
  content: '✔';
  position: absolute;
  top: .2em; left: .275em;
  font-size: 1.4em;
  line-height: 0.8;
  color: #2196F3;
  transition: all .2s;
  font-family: Helvetica, Arial, sans-serif;
}
/* checked mark aspect changes */
[type="checkbox"]:not(:checked) + label:after {
  opacity: 0;
  transform: scale(0);
}
[type="checkbox"]:checked + label:after {
  opacity: 1;
  transform: scale(1);
}
/* disabled checkbox */
[type="checkbox"]:disabled:not(:checked) + label:before,
[type="checkbox"]:disabled:checked + label:before {
  box-shadow: none;
  border-color: #bbb;
  background-color: #ddd;
}
[type="checkbox"]:disabled:checked + label:after {
  color: #999;
}
[type="checkbox"]:disabled + label {
  color: #aaa;
}

</style>
