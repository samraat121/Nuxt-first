<template>
  <div class="container">
    <h1 class="text-center">Customer Bio Table</h1>
    <div class="card">
      <div class="card-header">
        User Information
      </div>
      <div class="card-body">
        <table class="table">
          <thead>
            <tr>
              <th>#</th>
              <th>Name</th>
              <th>Email</th>
              <th>Action</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(customer, index) in customers" :key="customer.slug">
              <td># {{ index + 1 }}</td>
              <td> {{ customer.name }}</td>
              <td>{{ customer.email }}</td>
              <td>
                <nuxt-link :to="`customers/${customer.slug}`">Edit</nuxt-link>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
    <!-- <ul v-for="mountain in mountains" :key="mountain.slug">
      <li>{{mountain.name}}</li>
       <NuxtLink :to="`mountains/${mountain.slug}`">{{
          mountain.email
        }}</NuxtLink>
    </ul> -->
  </div>
</template>

<script>
// const axios = require('axios');
import axios from 'axios'
export default {
  data() {
    return {
      customers: {},
    }
  },

  mounted() {
    console.log('Component mounted.')
    this.getData()
  },
  methods: {
    getData() {
      axios
        .get('http://localhost:8000/api/customer')
        .then((response) => {
          this.customers = response.data
          console.log(response.data)
        })
        .catch((e) => {
          console.log(e)
        })
    },
  },
  // async asyncData({ $axios }) {
  //   const mountains = await $axios.$get(`http://localhost:8000/api/customer`)
  //   return { mountains }
  // }
}
</script>
