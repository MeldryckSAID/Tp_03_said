<script setup lang="ts">
import Card from "../components/card.vue";



const unObjet = {
    price: "12 800", 
    name: "Los Angeles",
    adresse: "122 Elm Street",
    bed: 7,
    bathroom: "4",
    mcarre: "69"

}


</script>

<template>
    <div>
        <p>Simple</p>
        <Card ></Card>
        <Card v-bind="{nom: 'France', prix:'2 000', lieux:'Bordeaux', bed:'5', bathroom: '3', space:'65'}"></Card>
        <Card v-bind="unObjet"></Card>
    </div>
</template>
