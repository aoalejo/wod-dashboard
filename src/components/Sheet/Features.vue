<template>
  <b-tabs
    vertical
    justified
    align-self="stretch"
    active-nav-item-class="featureTabSelected"
    active-tab-class="featureTabSelected"
    class="row d-flex flex-nowrap mb-1"
    nav-wrapper-class="col-2"
    content-class="col-10 overflow-auto content-class-custom"
    :style="'.nav-link.active {background-color:' + color + '}'"
  >
    <b-tab
      title-item-class="featureTab"
      title-link-class="featureTab"
      :title="attributes.name"
      lazy
      active
    >
      <div class="row flex-nowrap">
        <div
          class="row mx-0"
          v-for="(advCat, index) in attributes.values"
          :key="'advCat' + advCat.name + index"
        >
          <b-card
            border-variant="dark"
            header-bg-variant="dark"
            header-text-variant="white"
            :header="advCat.name"
            style="min-width: 175px"
            v-for="index in Math.ceil(advCat.values.slice().length / 3)"
            :key="'advCatSliced' + index"
            no-body
            class="flex-fill mx-1"
          >
            <b-list-group>
              <Value
                v-for="value in advCat.values.slice(
                  (index - 1) * 3,
                  (index - 1) * 3 + 3
                )"
                :key="'advVal' + value.name + value.name"
                :value="value"
                :sheet="sheet"
              />
            </b-list-group>
          </b-card>
        </div>
      </div>
    </b-tab>

    <b-tab
      title-item-class="featureTab"
      title-link-class="featureTab"
      v-for="(ability, index) in abilities"
      :key="'abilityTab' + index"
      lazy
      :title="ability.name"
    >
      <div class="row flex-nowrap">
        <b-card
          border-variant="dark"
          header-bg-variant="dark"
          header-text-variant="white"
          style="min-width: 175px"
          v-for="index in Math.ceil(
            ability.values.filter(checkIfZero).slice().length / 4
          )"
          :key="'abilityCard' + index"
          no-body
          class="ml-1 mr-1 flex-fill p-0 col-4"
        >
          <b-list-group>
            <Value
              v-for="value in ability.values
                .filter(checkIfZero)
                .slice((index - 1) * 4, (index - 1) * 4 + 4)"
              :key="'abilityVal' + value.name + value.name + Math.random()"
              :value="value"
              :sheet="sheet"
            />
          </b-list-group>
        </b-card>
      </div>
    </b-tab>

    <b-tab
      title-item-class="featureTab"
      title-link-class="featureTab"
      lazy
      :title="advantages.name"
    >
      <div class="row flex-nowrap">
        <div
          class="row flex-nowrap ml-1 mr-1"
          v-for="(advCat, index) in advantages.values"
          :key="'advCat' + advCat.name + index"
        >
          <b-card
            border-variant="dark"
            header-bg-variant="dark"
            header-text-variant="white"
            :header="advCat.name"
            style="min-width: 175px"
            v-for="index in Math.ceil(advCat.values.slice().length / 3)"
            :key="'advCatSliced' + index"
            no-body
            class="flex-fill p-0 mr-1 ml-1"
          >
            <b-list-group>
              <Value
                v-for="value in advCat.values.slice(
                  (index - 1) * 3,
                  (index - 1) * 3 + 3
                )"
                :key="'advVal' + value.name + value.name"
                :value="value"
                :sheet="sheet"
              />
            </b-list-group>
          </b-card>
        </div>
      </div>
    </b-tab>
  </b-tabs>
</template>

<script>
import EventBus from "../../eventBus";
import Value from "./Value";

export default {
  components: { Value },
  name: "Features",
  props: {
    color: String,
    attributes: Object,
    advantages: Object,
    abilities: Array,
    sheet: Object,
  },
  methods: {
    checkIfZero(value) {
      return value.value != 0;
    },
    featureTapped(feature) {
      EventBus.$emit("featureTapped", feature, this.sheet);
    },
  },
};
</script>
<style>
.content-class-custom {
  overflow-x: scroll !important;
}

.nav-tabs {
  overflow: hidden;
}

.list-group-item {
  padding: 8px !important;
}
.card-header {
  padding: 5px !important;
}
.featureTab {
  font-size: small;
  border-top-left-radius: 0rem !important;
  border-bottom-left-radius: 0rem !important;
  border-bottom-right-radius: 0.25rem;
  border-top-right-radius: 0.25rem;
  text-orientation: initial !important;
  overflow: hidden;
  text-overflow: clip;
  align-self: end;
  max-lines: 1;
  text-align: initial;
}

.featureTabSelected {
  border-width: 3px !important;
  border-color: #ffffff #bd00e000 #00418200 #383f46 !important;
}
</style>
