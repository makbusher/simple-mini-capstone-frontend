/* eslint-disable */
<script>
import axios from 'axios'

export default {
  data: function() {
    return {
      message: "Welcome to Vue.js!",
      year: "2023",
      location: "Chicago",
      products: [],
      newProductParams: {}
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
    },
    createProduct: function() {
      axios.post("http:localhost:3000/products.json", this.newProductParams).then((response) => {
        console.log("products create", response);
        this.products.push(response.data);
        this.newProductParams = {};
      })
      .catch((error) => {
        console.log("products create error", error.response);
      });
    },
  },
};
</script>

<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <h3>{{ year }}</h3>
    <p><button v-on:click="getData">Data</button></p>
    <h1>New Product</h1>
    <div>
      Name:
      <input type="text" v-model="newProductParams.name" />
      Price:
      <input type="text" v-model="newProductParams.price" />
      Description:
      <input type="text" v-model="newProductParams.description" />
      Inventory:
      <input type="text" v-model="newProductParams.inventory" />
      Supplier ID:
      <input type="text" v-model="newProductParams.supplier_id" />
      <button v-on:click="createProduct()">Create Product</button>
    </div>
    <h2>All Products</h2>
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
