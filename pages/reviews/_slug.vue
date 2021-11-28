<template lang="en">
  <div>
    <div>{{api.title}}</div>
  </div>
</template>
<script>
export default {
  async asyncData({ $content, params }) {
    const api = await $content('articles', params.slug).fetch()
    return { api }
  },
}
</script>
