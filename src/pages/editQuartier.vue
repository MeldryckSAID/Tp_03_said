<script setup lang="ts">
import Card from "../components/card.vue";
import { supabase } from "../supabase";
import FormulaireEditQuartier from "../components/FormulaireEditQuartier.vue";

console.log("supabase :", supabase); // pour vérifier et "garder" supabase dans le code

let { data: quartier, error } = await supabase.from("quartier").select("*");
console.log(quartier);
</script>

<template>
  <h2  class="text-xl font-bold text-center py-4 bg-black text-indigo-400">Editer les quartier sur supabase</h2>
  <FormulaireEditQuartier></FormulaireEditQuartier>
</template>
