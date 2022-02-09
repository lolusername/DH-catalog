<template>
  <main class="min-h-screen bg-gray-50 font-fort">
    <NavBar />
    <section class="container max-w-screen-lg mx-auto">
      <div
        class="
          p-6
          bg-red-50
          shadow-sm
          text-xl
          border-gray-800 border
          mb-16
          grid
          gap-6
        "
      >
        <h2 class="font-mono text-3xl font-bold">
          Digital Humanities Research & Documentation
        </h2>

        <p>
          Over the course of the Spring 2022 semester, researchers in
          conjunction with librarians at the Mina Rees Library, will help index
          digital projects cited in the
          <span class="italic"> Debates in Digital Humanities</span> book
          series, assist with preliminary data analysis and visualizations based
          on the resulting dataset, and document the process on this site.
        </p>
        <p>More Updates soon</p>
      </div>
      <div class="divide-y divide-gray-800">
        <h2>Latest Posts</h2>
        <section class="p-3" v-for="post in posts" :key="post._id">
          <h2 class="text-dh-blue text-3xl font-mono font-bold">
            {{ post.title }}
          </h2>
          <article class="font-bold my-2 text-xl">
            {{ post.author.title }}
          </article>
        </section>
      </div>
    </section>
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
.bg-dh-blue {
  background: #137ba2;
}
.lime-text {
  color: #84cc16;
}
a {
  @apply bg-gray-900 text-gray-50  hover:bg-red-900 rounded-xl px-1 pb-0.5;
}
</style>