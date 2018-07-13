<template>
  <div class="stripe" :class="{ chosen }">

    <div class="title">
      <div class="left">
        <span class="date">{{ text_date }}</span>
        <span class="duration">{{ text_duration }} мин</span>
      </div>

      <div class="right" @click="check">
        <i :class="['fas', icon]"></i>
        <span class="filename">&nbsp;{{ file }}</span>
      </div>
    </div>

    <div class="thumbnails strip">
      <img v-for="i in [1,2,3,4,5]" :src="`/${file}/${i}.jpg`" alt="" onclick="window.open(this.src)">
    </div>

  </div>
</template>

<script>
  // .sort(function (left, right) {
  //   return moment.utc(left.timeStamp).diff(moment.utc(right.timeStamp))
  // });

  export default {
    name: "Movie",
    props: {file: String, date: String, duration: String},
    computed: {
      icon() {
        return this.chosen ? 'fa-check-circle' : 'fa-plus-circle'
      },
      text_date() {
        return moment(this.date, "YYYY-MM-DD HH:mm:ssZ").calendar('2018-02-23').toLowerCase()
      },
      text_duration() {
        return moment.duration(this.duration).asMinutes() | 0
      }
    },
    data: () => ({
      scrollLeft: 0,
      chosen: false,
    }),
    methods: {
      check() {
        this.chosen = !this.chosen
        this.$emit('input', this.chosen)
      }
    }
  }
</script>

<style scoped>
  .stripe {
    padding-bottom: 2rem;
    background: transparent;
    color: #626262;
    position: relative;
  }

  .stripe.chosen {
    background: #8bc34a29
  }

  .title {
    color: #333;
    font-size: 0.9em;
    font-weight: bold;
    padding: 0.5rem;
    display: flex;
    justify-content: space-between;
  }

  .title .duration {
    font-size: 0.8em;
    vertical-align: top;
    margin-left: 0.5rem;
    display: inline-block;
    background: linear-gradient(45deg, #ff77d3 0%, #869bff 100%);
    color: white;
    cursor: pointer;
    padding: 0 5px;
    border-radius: 10px;
  }

  .title .left {
    display: flex;
    align-items: center;
  }

  .title .right {
    color: #b9b9b9;
  }

  .chosen .title .right {
    color: #8bc34a;
  }

  .strip {
    display: flex;
    overflow-x: auto;
    width: 100%;
  }

  img {
    max-height: 50px;
  }

  img:not(:last-of-type) {
    padding-right: 2px;
  }
</style>
