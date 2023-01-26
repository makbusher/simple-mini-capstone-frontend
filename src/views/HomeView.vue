/* eslint-disable */
<script>
import axios from 'axios'

export default {
  data: function() {
    return {
      message: "Welcome to Vue.js!",
      year: "2023",
      location: "Chicago",
      image: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTo3EwEdzdUs6GtLmGyFLcClr-UipWleLJApA&usqp=CAU",
      count: 0
    };
  },
  created: function() {},
  methods: {}
};
</script>

<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <h3>{{ year }}</h3>
    <img v-bind:src="image" />
    <p><button v-on:click="count++">Add Count</button></p>
    <p>Count is: {{ count }}</p>
    <p>{{ location }}</p>
    Location: <input type="text" v-model="location" />
  </div>
</template>

<style></style>
