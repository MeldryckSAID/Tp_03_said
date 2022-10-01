<script setup lang="ts">
import Card from "../components/card.vue";
import { supabase } from "../supabase";
import FormulaireSuppressionQuartier from "../components/FormulaireSuppressionQuartier.vue";


console.log("supabase :", supabase); // pour vérifier et "garder" supabase dans le code

let { data: quartier, error } = await supabase.from("quartier").select("*");
console.log(quartier);
</script>

<template>
  <h2 class="text-xl font-bold text-center py-4 bg-black text-indigo-400">Supprimer les quartier sur supabase</h2>
  <FormulaireSuppressionQuartier></FormulaireSuppressionQuartier>
</template>
