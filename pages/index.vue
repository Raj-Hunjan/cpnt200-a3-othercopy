<template>
  <section>
    <nav>
      <h2>Blog</h2>
      <ul>
        <li v-for="post in posts" :key="post.slug">
          <NuxtLink :to="`blog/${post.slug}`">{{ post.title }}</NuxtLink>
        </li>
      </ul>

      <h2>Cars</h2>
      <ul>
        <li v-for="cars in cars" :key="cars.slug">
          <NuxtLink :to="`cars/${cars.slug}`">{{ cars.title }}</NuxtLink>
        </li>
      </ul>

      <h2>Color</h2>
      <ul>
        <li v-for="color in color" :key="color.slug">
          <NuxtLink :to="`color/${color.slug}`">{{ color.title }}</NuxtLink>
        </li>
      </ul>
    </nav>
  </section>
</template>
<script>
export default {
  // Calls data from all three collections in the content folder
  async asyncData({ $content }) {
    const posts = await $content('blog').fetch()
    const cars = await $content('cars').fetch()
    const color = await $content('color').fetch()
    return {
      posts,
      cars,
      color
    }
  },
  head() {
    return {
      script: [{ src: 'https://identity.netlify.com/v1/netlify-identity-widget.js' }]
    }
  }
}
</script>
