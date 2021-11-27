<template>
  <div>
    <h1>{{ mountain.name }}</h1>
    <h2>{{ mountain.email }}</h2>
  </div>
</template>

<script>
export default {
  async asyncData({ $axios, params }) {
    const mountain = await $axios.$get(
      `http://localhost:8000/api/customer/${params.slug}`
    )
    return { mountain }
  }
}
</script>
<style scoped>
p {
  margin: 20px auto;
  max-width: 600px;
}
</style>
