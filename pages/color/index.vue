<template>
  <div>
    <ul>
      <li v-for="color in color" :key="color.slug">
        <NuxtLink v-bind:to="`color/${color.slug}`">{{ color.description }}</NuxtLink>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  async asyncData({ $content }) {
    const color = await $content('color').fetch()
    return {
      color
    }
  }
}
</script>
