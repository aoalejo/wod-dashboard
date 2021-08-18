<template>
  <div class="d-flex flex-wrap">
    <div class="row col-12 mx-1">
      <div
        class="flex-fill mx-0 p-0 mt-2 row"
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
          class="flex-fill p-0 mx-1"
        >
          <b-list-group>
            <Value
              v-for="value in advCat.values.slice(
                (index - 1) * 3,
                (index - 1) * 3 + 3
              )"
              :key="'advVal' + value.name + color"
              :value="value"
              :sheet="sheet"
            />
          </b-list-group>
        </b-card>
      </div>
    </div>

    <div class="row col-12 mx-1">
      <b-card
        class="ml-1 mr-1 flex-fill p-0 mt-2"
        border-variant="secondary"
        header-bg-variant="secondary"
        header-text-variant="white"
        title-item-class="featureTab"
        title-link-class="featureTab"
        :header="ability.name"
        no-body
        v-for="(ability, index) in abilities"
        :key="'abilityTab' + index"
        active
      >
        <div class="flex-nowrap">
          <b-list-group>
            <Value
              v-for="value in ability.values"
              :key="'abilityVal' + value.name + color + Math.random()"
              :value="value"
              :sheet="sheet"
            />
          </b-list-group>
        </div>
      </b-card>
    </div>

    <div
      class="d-flex flex-wrap col-12"
      title-item-class="featureTab"
      title-link-class="featureTab"
      lazy
      :title="advantages.name"
    >
      <div class="row flex-wrap">
        <div
          class="row flex-nowrap col-12 ml-1 mr-1 mt-2"
          v-for="(advCat, index) in advantages.values"
          :key="'advCat' + advCat.name + index"
        >
          <b-card
            border-variant="dark"
            header-bg-variant="dark"
            header-text-variant="white"
            :header="advCat.name"
            style="min-width: 175px"
            :key="'advCatSliced' + index"
            no-body
            class="flex-fill p-0 mr-1 ml-1"
          >
            <b-list-group>
              <Value
                v-for="value in advCat.values"
                :key="'advVal' + value.name + color"
                :value="value"
                :sheet="sheet"
              />
            </b-list-group>
          </b-card>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Value from "./Value";

export default {
  components: { Value },
  name: "FeaturesPopup",
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
