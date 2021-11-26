<template>
  <article>
    <h2> #3 {{ color.description }}</h2>
    <nuxt-content :document="color" />
  </article>
</template>

<script>
export default {
  async asyncData({ $content, params, error }) {
    try {
      const color = await $content(`color/${params.slug}`).fetch()
      return {
        color
      }
    } catch (e) {
      error('No article found')
    }
  }
}
</script>
