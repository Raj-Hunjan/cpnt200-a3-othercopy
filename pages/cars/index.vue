<template>
  <div>
    <ul>
      <li v-for="cars in cars" :key="cars.slug">
        <NuxtLink v-bind:to="`cars/${cars.slug}`">{{ cars.title }}</NuxtLink>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  async asyncData({ $content }) {
    const car = await $content('cars').fetch()
    return {
      car
    }
  }
}
</script>
