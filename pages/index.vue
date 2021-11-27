<template>
<div>
  <h1 class="text-center">Customer Bio Table</h1>
    <ul v-for="mountain in mountains" :key="mountain.id">
      <li>{{mountain.name}}</li>
    </ul>
</div>
</template>

<script>
export default {
  async asyncData({ $axios }) {
    const mountains = await $axios.$get(`http://localhost:8000/api/customer`)
    return { mountains }
  }
}
</script>
