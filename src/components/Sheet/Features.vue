<template>
  <b-tabs
    vertical
    justified
    align-self="stretch"
    active-nav-item-class="featureTabSelected"
    active-tab-class="featureTabSelected"
    :style="'.nav-link.active {background-color:' + color + '}'"
  >
    <b-tab
      title-item-class="featureTab"
      title-link-class="featureTab"
      title="Attributes"
      lazy
      active
    >
      Tab contents 1
    </b-tab>
    <b-tab
      title-item-class="featureTab"
      title-link-class="featureTab"
      lazy
      title="Habilities"
    >
      Tab contents 2
    </b-tab>

    <b-tab
      title-item-class="featureTab"
      title-link-class="featureTab"
      lazy
      title="Advantages"
    >
      Tab contents 3
    </b-tab>

    <b-tab
      title-item-class="featureTab"
      title-link-class="featureTab"
      lazy
      title="Merits/Defects"
    >
      Tab contents 3
    </b-tab>

    <b-tab
      title-item-class="featureTab"
      title-link-class="featureTab"
      lazy
      title="Consumables"
    >
      Tab contents 3
    </b-tab>
  </b-tabs>
</template>

<script>
export default {
  components: {},
  name: "Features",
  props: {
    color: String,
    attributes: Object,
    virtues: Object,
    points: Array,
    merits: Array,
    defects: Array,
    consumables: Array,
    path: Object,
    health: Object,
  },
};
</script>
<style>
.featureTab {
  font-size: small;
  border-top-left-radius: 0rem !important;
  border-bottom-left-radius: 0rem !important;
  border-bottom-right-radius: 0.25rem;
  border-top-right-radius: 0.25rem;
  text-orientation: initial !important;
  align-self: end;
  width: 100%;
  text-align: initial;
}

.featureTabSelected {
  border-width: 3px !important;
  border-color: #ffffff #bd00e000 #00418200 #383f46 !important;
}
</style>
