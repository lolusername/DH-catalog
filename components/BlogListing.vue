<template>
  <main>
    {{ posts }}
  </main>
</template>

<script>
import { groq } from '@nuxtjs/sanity'

export default {
  name: 'blogListing',
  async asyncData({ $sanity }) {
    const postQuery = groq`*[_type == "pkost"]{
      authors[]->{name, bio}
      }`

    const posts = await $sanity.fetch(postQuery)

    return { posts }
  },
}
</script>

<style>
</style>