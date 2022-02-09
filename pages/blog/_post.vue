<template>
  <section>
    <NavBar />
    <div class="container max-w-screen-md mx-auto mb-24">
      <h1
        class="
          mt-12
          text-dh-blue text-3xl
          font-mono font-bold
          underline
          text-center
        "
      >
        {{ post.title }}
      </h1>
      <h3 class="text-center uppercase font-bold">
        By {{ post.author.title }}
      </h3>
      <div>
        <SanityContent class="text-2xl post" :blocks="post.content" />
      </div>
    </div>
  </section>
</template>

<script>
import { groq } from '@nuxtjs/sanity'
export default {
  async asyncData({ params, $sanity }) {
    const postQuery = groq`*[_type == "post" && urlSlug.current == "${params.post}"][0]{
        ...,
        author->
        }`
    const post = await $sanity.fetch(postQuery)
    return { post }
  },
}
</script>

<style>
.text-dh-blue {
  color: #137ba2;
}
.post p {
  @apply my-6;
}
</style>