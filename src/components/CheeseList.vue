<template>

<div class="cheese-list" v-if="cheeses">

    
    <div class="wrapper">
        <div class="cheese-box" :class="cheese.fields.milk.toLowerCase().replace(/\s/g, '')" v-for="(cheese, index) in cheeses" :key="index" :value="index">
            <h3>{{ cheese.fields.cheese }}</h3>
            <cheese-info :cheese="cheese" :id="index"></cheese-info>
            
        </div>
    </div>
</div>
  
</template>

<script>
import CheeseInfo from "@/components/CheeseInfo.vue";

export default {
    name: "cheese-list-component",
    props: ["cheeses"],
    components: {
        "cheese-info": CheeseInfo
    }
}
</script>

<style>

ul {
    list-style-type: none;
}

.cheese-box {
    border-radius: 25px;
    border: 2px solid #73AD21;
    padding: 20px;

}

.wrapper {
  max-width: 940px;
  margin: 0 20px;
  display: grid;
  grid-gap: 10px;
}

.wrapper {
  display: grid;
  margin: 0 auto;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  grid-auto-rows: minmax(150px, auto);
}

/* tmp */

.btn {
  cursor: pointer;
  background: #27ae60;
  display: inline-block;
  padding: .5em 1em;
  color: #fff;
  border-radius: 3px;
}

.milk {
  font-size: 2em;
  padding: 0.5em 0.5em;
  margin: 0.5em;
  border-radius: 50%;
}

.sheepmilk {
  border: 2px solid purple;
  background: grey;
}

.cowmilk {
  border: 2px solid orange;
  background: orangered;
}

.goatmilk {
  border: 2px solid yellowgreen;
  background: yellow;
}

.btn:hover,
.btn:focus {
  background: #2ecc71;
}

.btn:active {
  background: #27ae60;
  box-shadow: 0 1px 2px rgba(0,0,0, .2) inset;
}

</style>