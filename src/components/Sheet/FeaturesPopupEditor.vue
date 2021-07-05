<template>
  <div class="d-flex flex-wrap">
    <JsonEditor
        :options="{
            confirmText: 'confirm',
            cancelText: 'cancel',
        }"
        :objData="sheet" 
        v-model="sheet" >
    </JsonEditor>
  </div>
</template>

<script>
export default {
  components: {},
  name: "FeaturesPopupEditor",
  props: {
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
