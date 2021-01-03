<template>
  <div class="home">
    <h1>{{ title }}</h1>
    <input type="text" v-model="searchTerm">


 <div class="container">
  <div v-for="ticket in filterBy(tickets, searchTerm, 'street_name')">

  <table class="table">
    <thead>
        <tr>
          <th scope="col">Date</th>
          <th scope="col">Street No</th>
          <th scope="col">Direction</th>
          <th scope="col">Street Name</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>{{ ticket.date  }}</td>
          <td>{{ ticket.street_no }} </td>
          <td>{{ ticket.direction  }} </td>
          <td>{{ ticket.street_name  }}</td>
        </tr>
      </tbody>
  </table>
  </div>
  </div>
</div>

</template>

<style>
</style>

<script>
import axios from "axios";
import Vue2Filters from "vue2-filters";

export default {
  data: function () {
    return {
      title: "(ur)in trouble",
      tickets: [],
      fields: ["date", "street_no", "direction", "street_name"],
      searchTerm: "",
    };
  },
  created: function () {
    axios.get("/api/tickets").then((response) => {
      console.log("these are all the tickets", response);
      this.tickets = response.data;
    });
  },
  methods: {},
  mixins: [Vue2Filters.mixin],
};
</script>