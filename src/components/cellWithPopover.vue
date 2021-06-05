<template>
  <div :id="'d' + difficulty + data.index">
    <b-popover
      :target="'d' + difficulty + data.index"
      triggers="hover"
      placement="top"
    >
      Dice: {{ data.index + 1 }}  <br>
    </b-popover>

    <b-popover
      :target="'d' + difficulty + data.index"
      triggers="hover"
      placement="right"
    >
      Difficulty: {{ difficulty }}
    </b-popover>   

    <span class="small cellBody">{{ this.formatLabel(data.value) }}</span>
  </div>
</template>

<script>
export default {
  name: "cellWithPopOver",
  props: {
    data: Object,
    difficulty: Number,
  },
  methods: {
    formatLabel(text) {
      if (text >= 10){
        return "+"
      }

      if(text < 0){
        return String(text).replace("-","")
      }

      return text

    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.cellBody {
  font-family: SFMono-Regular, Menlo, Monaco, Consolas, "Liberation Mono",
    "Courier New", monospace !important;
}
</style>
