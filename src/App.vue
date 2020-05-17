<template>
  <div id="app">
    <h1>French Cheeseopedia</h1>
    <cheese-list-component :cheeses="cheeses"></cheese-list-component>
  </div>
</template>

<script>
import { eventBus } from './main.js';
import CheeseList from "./components/CheeseList.vue";

export default {
  name: 'App',
  data(){
    return {
      cheeses: [],
      selectedMilk: "All",
      selectedCheeses: []
    }
  },
  components: {
    "cheese-list-component": CheeseList
  },
  methods: {
    getCheeses: function(){
      fetch("https://public.opendatasoft.com/api/records/1.0/search/?dataset=frenchcheese&rows=338")
      .then(result => result.json())
      .then(cheeses => this.cheeses = cheeses.records)
      .catch(error => console.log(error))
    },
    filtered () {
      const result = this.cheeses.filter(cheese => cheese.fields.milk === "Cow Milk")
      return this.selectedCheeses.push(result)
    }
  },
  mounted(){
    this.getCheeses();
    this.filtered();
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

body {
  margin: 40px;
  font-family: 'Open Sans', 'sans-serif';
  background-color: #fff;
  color: #444;
}

h1,
p {
  margin: 0 0 1em 0;
}



</style>
