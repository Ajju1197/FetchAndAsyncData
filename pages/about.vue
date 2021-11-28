<template lang="en">
  <div>
    <div v-for="blog in blogs" :key="blog.slug">
    <nuxt-link :to="`/reviews/${blog.slug}`">
    <h2>{{ blog.title }}</h2>
    <h2>{{ blog.slug }}</h2>
    </nuxt-link>
    </div>
  </div>
</template>
<script>
export default {
  async asyncData({ $content }) {
    const blogs = await $content('articles').fetch()
    return { blogs }
  },
}
</script>
