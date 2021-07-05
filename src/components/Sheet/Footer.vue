<template>
  <b-alert
    class="d-flex row p-1 m-0 h-100"
    align-self="stretch"
    show
    :style="'background: ' + info.color"
  >
    <b-badge
      class="d-flex flex-fill text-center justify-content-center"
      style="height: max-content"
    >
      {{ health.name }}
    </b-badge>
    <b-form-select
      v-for="(damage, index) in health.damage"
      :key="'HealthValue' + index"
      :options="health.types"
      :v-model="damage"
      :value="damage"
      size="sm"
      class="mt-0"
    ></b-form-select>
  </b-alert>
</template> 
<script>
export default {
  name: "Footer",
  props: {
    info: Object,
    health: Object,
  },
  mounted() {
    this.health.damage.forEach((damage) => {
      console.log(damage);
    });
  },
  methods: {
    addDamage() {},
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

.custom-select-sm {
  height: calc(1em + 0.5rem + 2px);
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 0.5rem;
  font-size: 0.875rem;
}
</style>
