<template>
  <div>
    <b-input-group size="sm" :prepend="value.name" :append="value.value">
      <b-form-rating       
        :value="value.value"
        class="m-0"
        :stars="max"
        size="sm"
        inline
        icon-full="circle-fill"
        icon-empty="circle"
        disabled
      ></b-form-rating>
    </b-input-group>
  </div>
</template>
<script>
export default {
  name: "Value",
  props: {
    value: Object,
    max: Number,
    showRaiting: Boolean,
  },
};
</script>
<style scoped>
.badge {
  overflow: hidden;
  text-overflow: ellipsis;
}
.alert {
  border-top-left-radius: 0.25rem;
  border-bottom-left-radius: 0.25rem;
  border-bottom-right-radius: 0rem;
  border-top-right-radius: 0rem;
}
</style>
