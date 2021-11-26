<template>
  <article>
    <h2> #2 {{ cars.title }}</h2>
    <nuxt-content :document="cars" />
  </article>
</template>

<script>
export default {
  async asyncData({ $content, params, error }) {
    try {
      const cars = await $content(`cars/${params.slug}`).fetch()
      return {
        cars
      }
    } catch (e) {
      error('No article found')
    }
  }
}
</script>
