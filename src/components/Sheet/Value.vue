<template>
  <div>
    <b-list-group-item
      class="d-flex justify-content-between align-items-center"
      v-on:click="featureTapped(value)"
      :title="value.name"
      :id="
        'ValueInfoPopOver' +
        hashOf(value.description + value.name + sheet.info.color)
      "
    >
      <span>{{ value.name }} </span>
      <span
        ><strong>{{ value.value }}</strong></span
      >
      <b-modal
        size="xl"
        hide-backdrop
        :id="
          'ValueInfoModal' +
          hashOf(value.description + value.name + sheet.info.color)
        "
        >{{ value.description }}</b-modal
      >
      <b-popover
        v-if="value.description.length > 1"
        :target="
          'ValueInfoPopOver' +
          hashOf(value.description + value.name + sheet.info.color)
        "
        triggers="hover"
        placement="top"
        boundary="viewport"
        class="d-flex p-2"
      >
        <template #title>{{ value.name }}</template>
        {{
          value.description.length > 200
            ? value.description.slice(0, 200) + "..."
            : value.description
        }}

        <div class="col-12 p-0">
          <b-button-group class="mt-4 col-12" size="sm">
            <b-button
              variant="info"
              v-on:click="restTo(index)"
              v-if="value.description.length > 200"
              v-b-modal="
                'ValueInfoModal' +
                hashOf(value.description + value.name + sheet.info.color)
              "
              >Ver completo
            </b-button>
          </b-button-group>
        </div>
      </b-popover>
    </b-list-group-item>
  </div>
</template>
<script>
import EventBus from "../../eventBus";

export default {
  name: "Value",
  props: {
    value: Object,
    sheet: Object,
  },
  methods: {
    hashOf(s) {
      return s.split("").reduce(function (a, b) {
        a = (a << 5) - a + b.charCodeAt(0);
        return a & a;
      }, 0);
    },
    featureTapped(feature) {
      EventBus.$emit("featureTapped", feature, this.sheet);
    },
  },
};
</script>
<style scoped>
.list-group-item {
  padding: 8px !important;
}
.card-header {
  padding: 5px !important;
}
</style>
