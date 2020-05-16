<template>
  <div id="app">

  </div>
</template>

<script>

export default {
  name: 'App',
  data(){
    return {
      cheeses: {}
    }
  },
  components: {
  },
  methods: {
    getCheeses: function(){
      fetch("https://public.opendatasoft.com/api/records/1.0/search/?dataset=frenchcheese")
      .then(result => result.json())
      .then(cheeses => this.cheeses = cheeses)
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
