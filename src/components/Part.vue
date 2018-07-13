<template>
  <div class="part" @click="isOn = !isOn" :class="{ highlight: isOn }">

    <div class="name">{{ d.title }}</div>

    <div class="thumbnails strip" v-on:scroll.passive="onScroll">
      <img v-for="i in [1,2,3,4,5]" :src="`/${d.file}/${i}.jpg`" alt="">

      <div class="strip parallax" ref="back">
        <img v-for="i in [1,2,3,4,5]" :src="`/${d.file}/${i}.jpg`" alt="">
      </div>
    </div>

  </div>
</template>

<script>
  export default {
    name: "Part",
    props: {d: Object},
    data: () => ({
      scrollLeft: 0,
      isOn: false
    }),
    methods: {
      onScroll(e) {
        this.$refs.back.scrollLeft = e.srcElement.scrollLeft
      }
    }
  }
</script>

<style scoped>
.part {
  padding-bottom: 2rem;
  margin-bottom: 1.5rem;
  background: transparent;
  color: #626262;
  position: relative;
}

.name {
  color: white;
  font-size: 0.9em;
  font-weight: bold;
  padding: 0.5rem;
}

.strip {
  display: flex;
  overflow-x: auto;
  width: 100%;
}

img {
  max-height: 160px;
  padding-right: 2px;
  width: 286px;
}

img:last-of-type {
  padding: 0;
}

.parallax {
  z-index: -1;
  height: 100%;
  position: absolute;
  filter: blur(15px);
  transform: scaleY(1.2);
  touch-action: none;
}

.parallax img {
  height: calc(100% + 2rem);
}

.highlight .thumbnails {
  filter: saturate(1.3) contrast(1.3) brightness(1.1)
}

.highlight .name {
  color: black;
}

</style>
