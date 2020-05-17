<template>
  <div id="app">
    <h1>French Cheeseopedia</h1>
    <h2>{{ selectedMilk }}</h2>
    <p>  
    <button @click="milkAction('Cow Milk')" class="btn milk cowmilk">🐄</button>
    <button @click="milkAction('Goat Milk')" class="btn milk goatmilk">🐐</button>
    <button @click="milkAction('Sheep Milk')" class="btn milk sheepmilk">🐑</button>
    </p>
    <cheese-list-component :cheeses="selectedCheeses"></cheese-list-component>
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
    milkAction(milk) {
      if (this.selectedMilk != milk) {
          this.selectedMilk = milk
      } else {
          this.selectedMilk = "All"
      }
      return this.selectedMilk
    }
  },
  mounted(){
    this.getCheeses();
  },
  computed: {
  filtered() {
      if (this.selectedMilk === "All" ) {
        return this.selectedCheeses = this.cheeses
      } else {
        const result = this.cheeses.filter(cheese => cheese.fields.milk === this.selectedMilk)
        return this.selectedCheeses = result
      }
    }
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
