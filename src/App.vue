<template>
  <div id="app">
    <div>
      <b-navbar toggleable="lg" type="dark" variant="info" class="w-100">
        <b-navbar-brand href="#">WoD Dashboard</b-navbar-brand>

        <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

        <b-collapse id="nav-collapse" is-nav>
          <!-- Right aligned nav items -->
          <b-navbar-nav class="ml-auto">
            <b-button v-b-toggle.sidebar-1>Open Help</b-button>
          </b-navbar-nav>
        </b-collapse>
      </b-navbar>

      <b-sidebar id="sidebar-1" title="Help" shadow class="p-0">
        <!--Ayuda-->
      </b-sidebar>
    </div>
    <div class="row justify-content-center p-0 m-0">
      <Rolls
        :sheets="sheets"
        class="col-lg-4 col-xl-3 col-md-12 col-sm-12 col-12 p-0 independent"
      />
      <Sheets
        :sheets="sheets"
        class="col-lg-8 col-xl-9 col-md-12 col-sm-12 col-12 p-0 independent"
      />
    </div>
  </div>
</template>

<script>
import Rolls from "./components/Rolls.vue";
import Sheets from "./components/Sheets.vue";

import karl from "../public/dataSheets/karl.json";
import phillippe from "../public/dataSheets/Phillippe.json";
import jonathan from "../public/dataSheets/jonathan.json";
import claire from "../public/dataSheets/claire.json";
import anderson from "../public/dataSheets/anderson.json";

export default {
  name: "App",
  components: {
    Rolls,
    Sheets,
  },
  data: function () {
    return {
      sheets: [],
    };
  },
  mounted() {
    this.sheets.push(karl);
    this.sheets.push(phillippe);
    this.sheets.push(jonathan);
    this.sheets.push(claire);
    this.sheets.push(anderson);
  },
};
</script>

<style>
.independent {
  height: 90vh;
  overflow: scroll;
}
.col-auto {
  padding: 0 !important;
  margin: 0 !important;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
