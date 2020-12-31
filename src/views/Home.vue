<template>
  <div class="home">
    <h1>{{ message }}</h1>
 
<div class="container">
  <table class="table">
  <thead>
    <tr>
      <th scope="col">Date</th>
      <th scope="col">Street No.</th>
      <th scope="col">Street Direction</th>
      <th scope="col">Street Name</th>
    </tr>
  </thead>
  <tbody>
  <div v-for="ticket in tickets">
    <tr>
      <td>{{ticket.date}}</td>
      <td>{{ticket.street_no}}</td>
      <td>{{ticket.direction}}</td>
      <td>{{ticket.street_name}}</td>
    </tr>
  </div>
  </tbody>
   </table>
    </div>
  </div>
</template>

<style>
</style>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      message: "(ur)in trouble",
      tickets: [],
    };
  },
  created: function () {
    axios.get("/api/tickets").then((response) => {
      console.log("these are all the tickets", response);
      this.tickets = response.data;
    });
  },
  methods: {},
};
</script>