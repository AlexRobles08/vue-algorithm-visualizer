<template>
  <div class="algorithm-visualizer">
    <div v-for="(number, index) in randomArray" :key="index">{{ number }}</div>
    <button v-on:click="generateRandomArray">Generate Random Array</button>
  </div>
</template>

<script>
export default {
  name: "AlgorithmVisualizer",
  data: function() {
    return {
      randomArray: [],
      sortedArray: []
    };
  },
  methods: {
    generateRandomArray: function() {
      for (let i = 0; i < 100; i++) {
        this.randomArray.push(Math.floor(Math.random() * (100 - 5 + 1) + 5));
      }
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>