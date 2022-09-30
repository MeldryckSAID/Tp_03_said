<script setup lang="ts">
    import Card from "../components/card.vue";
    import { supabase } from "../supabase";

console.log("supabase :", supabase); // pour vérifier et "garder" supabase dans le code

let { data: Maisons, error } = await supabase
  .from('Maisons')
  .select('*')
console.log(Maisons);




</script>
        
    
<template>
<h2 class="text-center">Liste avec supabase</h2>
    <div class="flex flex-row" >
        
        <div  v-for="m in Maisons" :key="m">
        <Card v-bind="m"></Card>

        </div>
      
    </div>
</template>
