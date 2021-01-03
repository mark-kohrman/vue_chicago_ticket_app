<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <div>  
      <b-table hover :items="tickets" :fields="fields"></b-table>
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
      message: "(ur)in trouble!!!",
      tickets: [],
      fields: ["date", "street_no", "direction", "street_name"],
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