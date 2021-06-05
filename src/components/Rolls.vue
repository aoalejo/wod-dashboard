<template>
  <div class="rolls">
    <b-card no-body class="m-2">
      <b-button class="flex-fill" v-on:click="makeRoll">Make Roll!</b-button>

      <b-button-group class="d-flex col-12 mt-2">
        <b-button
          size="sm"
          class="text-monospace"
          :variant="buttonColor(singleRoll)"
          v-for="(singleRoll, index) in roll.slice(0, 10)"
          :key="index"
          v-b-popover.hover.top="''"
          :title="singleRoll"
        >
          {{ singleRoll }}
        </b-button>
      </b-button-group>

      <b-button-group class="d-flex col-12 mt-2 mb-2">
        <b-button
          size="sm"
          :variant="buttonColor(singleRoll)"
          class="text-monospace"
          v-for="(singleRoll, index) in roll.slice(10, 20)"
          :key="index"
          v-b-popover.hover.top="''"
          :title="singleRoll"
        >
          {{ singleRoll }}
        </b-button>
      </b-button-group>

      <b-table
        class="m-0 p-0"
        small
        :fields="columns"
        :items="results"
        hover
        responsive
        fixed
        ref="table"
      >
        <template #cell(difficulty)="data">
          <small>{{ data.index + 1 }}</small>
        </template>

        <template #cell(d1)="data">
          <cell-with-popover :data="data" :difficulty="1"></cell-with-popover>
        </template>

        <template #cell(d2)="data">
          <cell-with-popover :data="data" :difficulty="2"></cell-with-popover>
        </template>

        <template #cell(d3)="data">
          <cell-with-popover :data="data" :difficulty="3"></cell-with-popover>
        </template>

        <template #cell(d4)="data">
          <cell-with-popover :data="data" :difficulty="4"></cell-with-popover>
        </template>

        <template #cell(d5)="data">
          <cell-with-popover :data="data" :difficulty="5"></cell-with-popover>
        </template>

        <template #cell(d6)="data">
          <cell-with-popover :data="data" :difficulty="6"></cell-with-popover>
        </template>

        <template #cell(d7)="data">
          <cell-with-popover :data="data" :difficulty="7"></cell-with-popover>
        </template>

        <template #cell(d8)="data">
          <cell-with-popover :data="data" :difficulty="8"></cell-with-popover>
        </template>

        <template #cell(d9)="data">
          <cell-with-popover :data="data" :difficulty="9"></cell-with-popover>
        </template>

        <template #cell(d10)="data">
          <cell-with-popover :data="data" :difficulty="10"></cell-with-popover>
        </template>
      </b-table>

      <b-card
        class="m-2"
        v-for="(singleRoll, index) in rolls
          .slice(Math.max(rolls.length - 5, 0), rolls.length)
          .reverse()"
        :key="'Historic' + index"
        head
      >
        <template #header>
          <h4 class="mb-0">{{ singleRoll.time }}</h4>
        </template>
        {{ printParticularRoll(singleRoll.roll) }}
      </b-card>

      <b-button v-b-toggle.collapse-1 variant="primary">View All</b-button>

      <b-collapse id="collapse-1" class="mt-2">
        <b-card
          class="m-2"
          v-for="(singleRoll, index) in rolls.slice().reverse()"
          :key="'Historic' + index"
          head
        >
          <template #header>
            <h4 class="mb-0">{{ singleRoll.time }}</h4>
          </template>
          {{ printParticularRoll(singleRoll.roll) }}
        </b-card>
      </b-collapse>
    </b-card>
  </div>
</template>

<script>
import cellWithPopover from "./cellWithPopover.vue";
export default {
  components: { cellWithPopover },
  name: "Rolls",
  data: function () {
    return {
      roll: [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
      rolls: [],
      columns: [
        // A virtual column that doesn't exist in items
        { key: "difficulty", stickyColumn: true, label: "" },
        { key: "d2", label: "2" },
        { key: "d3", label: "3" },
        { key: "d4", label: "4" },
        { key: "d5", label: "5" },
        { key: "d6", label: "6" },
        { key: "d7", label: "7" },
        { key: "d8", label: "8" },
        { key: "d9", label: "9" },
        { key: "d10", label: "0" },
      ],
      results: [
        {},
        {},
        {},
        {},
        {},
        {},
        {},
        {},
        {},
        {},
        {},
        {},
        {},
        {},
        {},
        {},
        {},
        {},
        {},
        {},
      ],
    };
  },
  mounted() {
    this.makeRoll();
  },
  methods: {
    labelForTable(index) {
      return "(" + this.roll[index] + ")";
    },
    passed(dificulty, numberOfDice, diceRoll) {
      var quantityPassed = 0;
      diceRoll.slice(0, numberOfDice).forEach((roll) => {
        if (roll >= dificulty) {
          quantityPassed++;
        }
        if (roll == 1) {
          quantityPassed--;
        }
        if (roll == 10) {
          quantityPassed++;
        }
      });

      return quantityPassed;
    },
    printRoll() {
      var text = "";

      var i;
      for (i = 0; i < this.roll.length; i++) {
        if (i % 5 == 0) {
          text += "\n\r";
        }
        text += " " + this.roll[i];
      }

      return text;
    },
    printParticularRoll(roll) {
      var text = "";

      var i;
      for (i = 0; i < roll.length; i++) {
        if (i % 5 == 0) {
          text += "\n\r";
        }
        text += " " + roll[i];
      }

      return text;
    },
    cellColor(result) {
      if (result < 0) {
        return "danger";
      }

      if (result == 0) {
        return "warning";
      }

      if (result == 1) {
        return "primary";
      }

      if (result == 2) {
        return "info";
      }

      if (result >= 3) {
        return "success";
      }
    },
    buttonColor(value) {
      if (value <= 1) {
        return "danger";
      }

      if (value <= 3) {
        return "warning";
      }

      if (value <= 6) {
        return "primary";
      }

      if (value <= 9) {
        return "info";
      }

      if (value <= 10) {
        return "success";
      }
    },
    makeRoll() {
      var newRoll = [];
      var today = new Date();
      var timeStr = today.toLocaleDateString() + ' ' + today.toLocaleTimeString();
        //today.getHours() + ":" + today.getMinutes() + ":" + today.getSeconds();

      var i;
      for (i = 0; i < 20; i++) {
        var newDice = this.rando(1, 10);
        newRoll.push(newDice);
      }

      this.roll = newRoll;

      var dice = 0;
      for (dice = 0; dice < 20; dice++) {
        this.results[dice]["_cellVariants"] = [];

        var diff = 0;
        for (diff = 0; diff < 9; diff++) {
          var columnName = "d" + (diff + 2);

          var result = this.passed(diff + 2, dice + 1, newRoll);

          this.results[dice][columnName] = result;

          this.results[dice]["_cellVariants"][columnName] = this.cellColor(
            result
          );
        }
      }

      this.rolls.push({ time: timeStr, roll: newRoll });
      this.$refs.table.refresh();
    },
    rando(min, max) {
      return (
        (Math.floor(Math.pow(10, 14) * Math.random() * Math.random()) %
          (max - min + 1)) +
        min
      );
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
table {
  font-family: SFMono-Regular, Menlo, Monaco, Consolas, "Liberation Mono",
    "Courier New", monospace !important;
  padding: 0px;
  margin: 0px;
}
.card-header {
  padding: 0px;
}
</style>
