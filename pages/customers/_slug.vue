<template>
  <div>
    <h1>{{ customer.name }}</h1>
    <h2>{{ customer.email }}</h2>
  </div>
</template>

<script>
export default {
  async asyncData({ $axios, params }) {
    const customer = await $axios.$get(
      `http://localhost:8000/api/customer/${params.slug}`
    )
    return { customer }
  }
}
</script>
<style scoped>
p {
  margin: 20px auto;
  max-width: 600px;
}
</style>
