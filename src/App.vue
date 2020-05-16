<template>
  <div id="app">
    <h1>French Cheeseopedia</h1>
    <cheese-list-component :cheeses="cheeses"></cheese-list-component>
  </div>
</template>

<script>
import CheeseList from "./components/CheeseList.vue";

export default {
  name: 'App',
  data(){
    return {
      cheeses: {}
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
    }
  },
  mounted(){
    this.getCheeses();
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
</style>
