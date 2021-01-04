<template>
  <div class="home">

    <h2> Filter By Street Name </h2>
    <input type="text" placeholder="Enter street name" v-model="searchTerm">


    <div class="container">
    <!-- <div>  
      <b-table hover :items="tickets" :fields="fields"></b-table>
   </div> --> 
  <div>

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
        <tr v-for="ticket in filterBy(tickets, searchTerm, 'street_name')">
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
      tickets: [],
      fields: ["date", "street_no", "direction", "street_name"],
      searchTerm: "",
      filters: {
        streetName: "",
      },
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