<template lang="en">
  <div  class="main-loop">
    <div  v-for="planet in planets" :key="planet.slug">
      <nuxt-link :to="`${planet.slug}`">
       <div class="img">
       <li class="title">{{planet.title}}</li>
       <img format="webp" quality="80" fit="cover" width="300" height="169"   :src="planet.image" :alt="planet.title"/>
       </div>
      </nuxt-link>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      planets: [],
      // error: '',
    }
  },
  // transition: 'fade',
  async fetch() {
    const api = 'https://api.nuxtjs.dev/planets'
    this.planets = await fetch(api).then((res) => {
      return res.json()
    })
  },
}
</script>
<style scoped>
.main-loop {
  width: 100%;
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  flex-wrap: wrap;
  grid-row-gap: 1em;
}
.img {
  position: relative;
  cursor: pointer;
}
.img img {
  width: 100%;
  height: 100%;
}
.title {
  position: absolute;
  top: 0;
  left: 0;
  color: #fff;
  font-size: 30px;
  background: #000;
}
@media (max-width: 576px) {
  .main-loop {
    width: 100%;
    grid-template-columns: 1fr;
  }
  .img {
    margin: 0 auto;
  }
}
</style>
