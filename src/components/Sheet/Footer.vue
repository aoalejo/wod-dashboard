<template>
  <b-alert
    align-v="stretch"
    class="d-flex row p-0 m-0 h-100"
    align-self="stretch"
    show
    :variant="info.color"
  >
    <b-form-select
      v-for="i in health.max"
      :key="'HealthValue' + i"
      :options="health.types"
      :v-model="health.damage[i]"
      size="sm"
      class="mt-0"
    ></b-form-select>
  </b-alert>
</template>
 "health": {
    "max": 7,
    "damage": [
      1,
      3
    ],
    "types": [
      "Contundente",
      "No letal",
      "Letal",
      "Agravado"
    ]
  }
<script>
export default {
  name: "Footer",
  props: {
    info: Object,
    health: Object,
  },
};
</script>
<style scoped>
.badge {
  overflow: hidden;
  text-overflow: ellipsis;
}
.alert {
  border-top-right-radius: 0.25rem;
  border-bottom-right-radius: 0.25rem;
  border-bottom-left-radius: 0rem;
  border-top-left-radius: 0rem;
}
</style>
