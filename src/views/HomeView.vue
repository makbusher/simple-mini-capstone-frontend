/* eslint-disable */
<script>
import axios from 'axios'

export default {
  data: function() {
    return {
      message: "Welcome to Vue.js!",
      year: "2023",
      location: "Chicago",
      products: []
    };
  },
  created: function() {
    this.getData()
  },
  methods: {
    getData: function() {
      axios.get("http://localhost:3000/products.json").then(response => {
        this.products = response.data
        console.log(response.data)
      })
    }
  }
};
</script>

<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <h3>{{ year }}</h3>
    <p><button v-on:click="getData">Data</button></p>
    <div v-for="product in products" v-bind:key="product.id">
      <h3>{{ product.name }}</h3>
      <p> {{ product.price }}</p>
      <p> {{ product.description }}</p>
      <hr />
    </div>
    <p>{{ location }}</p>
  </div>
</template>

<style></style>
