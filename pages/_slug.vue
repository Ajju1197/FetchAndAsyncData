<template lang="en">
  <div class="mountain">
    <div class="mountain_block">
      <div v-if="error"><Error :message="error.message"/></div>
      <span v-else @click="goBack">
      <div class="planet-img">
        <img :src="mountain.image"/>
      </div>
      <h1 class="title">{{mountain.slug}}</h1>
    </span>
    </div>
  </div>
</template>
<script>
export default {
  async asyncData({ params }) {
    const mountain = await fetch(
      `http://api.nuxtjs.dev/planets/${params.slug}`
    ).then((res) => {
      if (res.ok) {
        return res.json()
      }
      throw new Error(res.status)
    })
    return { mountain }
  },
  data() {
    return {
      error: '',
    }
  },
  methods: {
    goBack() {
      return this.$router.go(-1)
    },
  },
}
</script>
<style scoped>
.mountain {
  height: 100vh;
  background: darkblue;
  color: #fff;
}
span {
  padding: 10px 20px;
  /* background: green; */
  color: #fff;
  border-radius: 8px;
  border: none;
  cursor: pointer;
  margin-top: 4em;
}
.mountain_block {
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
.planet-img {
  width: 300px;
  height: 500px;
}
.planet-img img {
  width: 100%;
  height: 100%;
}
h1 {
  color: #fff;
  font-size: 20px;
  font-weight: bold;
}
</style>
