<template>
  <div class="sheets">
    <b-card
      class="m-1 p-0 mb-2"
      v-for="(sheet, index) in sheets"
      :key="'sheet' + index"
      no-body
    >
      <div class="row m-0 p-0 row-eq-height">
        <div class="col-2 m-0 p-0" align-self="stretch">
          <Header :info="sheet.info" :sheet="sheet" />
        </div>
        <div
          :class="
            (sheet.health ? ' col-9 ' : ' col-10 ') +
            ' m-0 p-0 d-flex flex-wrap'
          "
        >
          <Features
            class="col-12 m-0 p-0"
            :color="sheet.info.color"
            :abilities="sheet.abilities"
            :attributes="sheet.attributes"
            :advantages="sheet.advantages"
            :sheet="sheet"
          />
          <Consumables
            class="col-12"
            :consumables="sheet.consumables"
            :info="sheet.info"
          />
        </div>
        <div class="col-1 m-0 p-0" align-self="stretch">
          <Footer
            :info="sheet.info"
            :health="sheet.health"
            v-if="sheet.health"
          />
        </div>
      </div>
    </b-card>
  </div>
</template>

<script>
import Header from "./Sheet/Header.vue";
import Consumables from "./Sheet/Consumables.vue";
import Footer from "./Sheet/Footer.vue";
import Features from "./Sheet/Features.vue";

export default {
  components: { Header, Consumables, Features, Footer },

  name: "Sheets",
  data: function () {
    return {
      roll: [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
      rolls: [],
    };
  },
  props: {
    sheets: Array,
  }
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
