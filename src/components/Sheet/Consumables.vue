<template>
  <div class="p-0 m-0">
    <b-progress
      class="p-0 m-0"
      v-for="(consumable, index) in consumables"
      :key="'consumable' + index + info.color + info.name"
      :id="'consumable' + index + info.color + info.name"
      :value="consumable.value.now"
      striped
      :max="consumable.value.max"
      :variant="consumable.color"
    >
      <b-progress-bar :value="consumable.value.now">
        <span>
          {{ consumable.name }}: {{ consumable.value.now }} /
          {{ consumable.value.max }}</span
        >
      </b-progress-bar>
    </b-progress>
    <b-popover
      :target="'consumable' + index + info.color + info.name"
      triggers="hover"
      placement="top"
      class="d-flex p-2"
      v-for="(consumable, index) in consumables"
      :key="'popconsumable' + index + info.color + info.name"
    >
      <template #title>{{
        consumable.name +
        ": " +
        consumable.value.now +
        "/" +
        consumable.value.max
      }}</template>
      {{ consumable.description }}

      <div class="col-12 p-0">
        <b-button-group class="mt-4 col-12" size="lg">
          <b-button variant="danger" v-on:click="restTo(index)">
            <b-icon icon="dash"
          /></b-button>
          <b-button variant="success" v-on:click="addTo(index)"
            ><b-icon icon="plus"
          /></b-button>
        </b-button-group>
      </div>
    </b-popover>
  </div>
</template>
<script>
export default {
  name: "Consumables",
  props: {
    consumables: Array,
    info: Object,
  },
  methods: {
    addTo(index) {
      this.consumables[index].value.now = this.consumables[index].value.now + 1;
    },
    restTo(index) {
      this.consumables[index].value.now = this.consumables[index].value.now - 1;
    },
  },
};
</script>
<style scoped>
.progress {
  border-radius: 0rem;
}
</style>
