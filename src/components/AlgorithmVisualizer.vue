<template>
  <div class="algorithm-visualizer">
    <div class="random-array-wrapper" v-if="!showSortedArray">
      <div
        v-for="(number, index) in randomArray"
        :key="index"
        :style="{'height':`${number*3}px`}"
        class="array-bar"
      ></div>
    </div>
    <div class="sorted-array-wrapper" v-if="showSortedArray">
      <div
        v-for="(number, index) in sortedArray"
        :key="index"
        :style="{'height':`${number}px`, 'background-color': color}"
        class="array-bar"
      ></div>
    </div>
    <button v-on:click="generateRandomArray">Generate Random Array</button>
    <button v-on:click="sortArray">Sort Array</button>
    <button v-on:click="sortSameArray">Sort Same Array</button>
  </div>
</template>

<script>
import Vue from "vue";

export default {
  name: "AlgorithmVisualizer",
  data: function() {
    return {
      randomArray: [],
      sortedArray: [],
      showSortedArray: false,
      color: "red"
    };
  },
  methods: {
    generateRandomArray: function() {
      this.randomArray = [];
      for (let i = 0; i < 200; i++) {
        this.randomArray.push(Math.floor(Math.random() * (100 - 5 + 1) + 5));
      }
      this.showSortedArray = false;
    },
    sortArray: function() {
      this.sortedArray = this.randomArray;
      for (let i = this.sortedArray.length - 1; i > 1; i--) {
        for (let j = 0; j < i; j++) {
          if (this.sortedArray[j] > this.sortedArray[j + 1]) {
            let temp = this.sortedArray[j];
            this.sortedArray[j] = this.sortedArray[j + 1];
            this.sortedArray[j + 1] = temp;
          }
        }
      }
      this.showSortedArray = true;
    },
    sortSameArray: function() {
      for (let i = this.randomArray.length - 1; i > 1; i--) {
        for (let j = 0; j < i; j++) {
          if (this.randomArray[j] > this.randomArray[j + 1]) {
            let temp = this.randomArray[j];
            // eslint-disable-next-line no-undef
            Vue.set(this.randomArray, j, this.randomArray[j + 1]);
            this.randomArray[j + 1] = temp;
          }
        }
      }
      console.log(this.randomArray);
      this.showSortedArray = false;
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.sorted-array-wrapper {
  min-height: 400px;
}
.array-bar {
  display: inline-block;
  width: 2px;
  margin: 0 1px;
  background-color: pink;
}
button {
  margin: 10px 10px;
}
</style>