<template>

<div class="cheese-list" v-if="cheeses">
    <h2>List of Cheese</h2>
        <ul>
            <li v-for="(cheese, index) in cheeses" :key="index" :value="index">
                {{ cheese.fields.cheese }}
            </li>
        </ul>
</div>
  
</template>

<script>
export default {
    name: "cheese-list-component",
    props: ["cheeses"]
}
</script>

<style>

</style>