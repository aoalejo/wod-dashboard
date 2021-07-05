<template>
  <div>
    <b-list-group-item
      class="d-flex justify-content-between align-items-center"
      v-b-popover.hover.top="value.description"
      v-on:click="featureTapped(value)"
      :title="value.name"
    >
      <span>{{ value.name }} </span>
      <span
        ><strong>{{ value.value }}</strong></span
      >
    </b-list-group-item>
  </div>
</template>
<script>
import EventBus from '../../eventBus'

export default {
  name: "Value",
  props: {
    value: Object,
  },
  methods: {
    featureTapped(feature) {
      EventBus.$emit("featureTapped", feature);
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
