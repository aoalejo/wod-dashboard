<template>
  <b-alert class="p-2 m-0 h-100" align-self="stretch" show :variant="info.color">
    <h4>
      <strong>
        {{ info.name }}
      </strong>
    </h4>
    <span>({{ info.player }})</span>

    <div class="row d-flex m-1">
      <b-badge
        class="flex-fill m-1"
        v-b-popover.hover.top="info.nature.description"
        :title="info.name + ' nature'"
      >
        {{ info.nature.name }}
      </b-badge>

      <b-badge
        class="flex-fill m-1"
        v-b-popover.hover.top="info.demeanor.description"
        :title="info.name + ' demeanor'"
      >
        {{ info.demeanor.name }}
      </b-badge>

      <b-badge
        class="flex-fill m-1"
        v-b-popover.hover.top="info.concept.description"
        :title="info.name + ' concept'"
      >
        {{ info.concept.name }}
      </b-badge>

      <b-badge
        class="flex-fill m-1"
        v-b-popover.hover.top="info.type.description"
        :title="info.name + ' type'"
      >
        {{ info.type.name }}
      </b-badge>

      <b-badge
        class="flex-fill m-1"
        v-b-popover.hover.top="info.power.description"
        :title="info.name + ' power'"
      >
        {{ info.power.name }}
      </b-badge>

      <b-badge
        class="flex-fill m-1"
        v-b-popover.hover.top="info.superior.description"
        :title="info.name + ' superior'"
      >
        {{ info.superior.name }}
      </b-badge>

      <b-badge
        class="flex-fill m-1"
        v-b-popover.hover.top="info.weakness.description"
        :title="info.name + ' weakness'"
      >
        {{ info.weakness.name }}
      </b-badge>
    </div>
  </b-alert>
</template>

<script>
export default {
  name: "Header",
  props: {
    info: Object,
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
