<template>
  <main class="min-h-screen bg-gray-50">
    <NavBar />
    <div class="grid grid-cols-3 container mx-auto gap-24">
      <section class="" v-for="post in posts" :key="post._id">
        <h2 class="lime-text text-3xl font-mono font-bold">
          {{ post.title }}
        </h2>
        <article class="text-dh-blue font-sans font-bold font-bold">
          {{ post.author.title }}
        </article>
        <SanityContent class="text-xl" :blocks="post.content" />
      </section>
    </div>
  </main>
</template>

<script>
import { groq } from '@nuxtjs/sanity'

export default {
  name: 'blogListing',
  async asyncData({ $sanity }) {
    const postQuery = groq`*[_type == "post"]{
      ...,
      author->
    }`
    const posts = await $sanity.fetch(postQuery)
    return { posts }
  },
}
</script>

<style scoped>
.text-dh-blue {
  color: #137ba2;
}
.lime-text {
  color: #84cc16;
}
a {
  @apply bg-gray-900 text-gray-50  hover:bg-red-900 rounded-xl px-1 pb-0.5;
}
</style>