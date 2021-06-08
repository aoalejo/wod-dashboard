<template>
  <div class="p-0 m-0">
    <b-progress
      class="p-0 m-0"
      v-for="(consumable, index) in consumables"
      :key="'consumable' + index"
      :value="consumable.value.now"
      striped
      :max="consumable.value.max"
      :variant="consumable.color"
      v-b-popover.hover.top="consumable.description"
      :title="
        consumable.name +
        ': ' +
        consumable.value.now +
        '/' +
        consumable.value.max
      "
    >
      <b-progress-bar :value="consumable.value.now">
        <span>
          {{ consumable.name }}: {{ consumable.value.now }} /
          {{ consumable.value.max }}</span
        >
      </b-progress-bar>
    </b-progress>
  </div>
</template>
{
      "name": "Fuerza de voluntad",
      "color": "#37a10a",
      "perTurn": 1,
      "value": {
        "max": 8,
        "now": 8
      },
      "description": "-"
    }
<script>
export default {
  name: "Consumables",
  props: {
    consumables: Array,
  },
};
</script>
<style scoped>
.progress {
  border-radius: 0rem;
}
</style>
