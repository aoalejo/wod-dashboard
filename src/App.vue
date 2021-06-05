<template>
  <div id="app">
    <div>
      <b-navbar toggleable="lg" type="dark" variant="info">
        <b-navbar-brand href="#">WoD Dashboard</b-navbar-brand>

        <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

        <b-collapse id="nav-collapse" is-nav>
          <!-- Right aligned nav items -->
          <b-navbar-nav class="ml-auto">
            <b-button v-b-toggle.sidebar-1>Open Help</b-button>
          </b-navbar-nav>
        </b-collapse>
      </b-navbar>

      <b-sidebar id="sidebar-1" title="Rolls" shadow class="p-0" >
        <!--Ayuda-->
      </b-sidebar>
    </div>
    <div class="d-flex">
      <Rolls class="col-lg-4 col-xl-3 col-md-6 col-sm-12 col-12"/>
      <Rolls />
    </div>
  </div>
</template>

<script>
import Rolls from "./components/Rolls.vue";

export default {
  name: "App",
  components: {
    Rolls,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
