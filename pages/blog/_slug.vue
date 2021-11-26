<template>
  <article>
    <h2> #1 {{ post.title }}</h2>
    <nuxt-content :document="post" />
  </article>
</template>

<script>
export default {
  async asyncData({ $content, params, error }) {
    try {
      const post = await $content(`blog/${params.slug}`).fetch()
      return {
        post
      }
    } catch (e) {
      error('No article found')
    }
  }
}
</script>
