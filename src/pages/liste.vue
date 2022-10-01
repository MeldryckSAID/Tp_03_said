<script setup lang="ts">
import Card from "../components/card.vue";
import Maisons from "@/assets/Maisons.json";
console.log(Maisons);
</script>

<template>

    <p  class="text-xl font-bold text-center py-4 bg-black text-indigo-400">Liste</p>

    <div class="flex flex-row justify-center">
      <Card v-for="m in Maisons" :key="m" v-bind="m"></Card>
    </div>
    

</template>
