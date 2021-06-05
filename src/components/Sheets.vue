<template>
  <div class="sheets">
    <b-card class="m-2" no-body>
      <b-table
        class="p-0"
        small
        :fields="columns"
        :items="sheets"
        hover
        responsive
        fixed
        sticky-header
        style="height: 100vh"
        ref="table"
      >
      </b-table>
    </b-card>
  </div>
</template>

<script>
export default {
  name: "Sheets",
  data: function () {
    return {
      roll: [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
      rolls: [],
      columns: ["Sheet", "Sheet"],
      sheets: [
          { isActive: true, age: 40, first_name: 'Dickerson', last_name: 'Macdonald' },
          { isActive: false, age: 21, first_name: 'Larsen', last_name: 'Shaw' },
          { isActive: false, age: 89, first_name: 'Geneva', last_name: 'Wilson' },
          { isActive: true, age: 38, first_name: 'Jami', last_name: 'Carney' }
        ],
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
