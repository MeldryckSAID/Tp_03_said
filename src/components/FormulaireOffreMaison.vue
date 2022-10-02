<script setup lang="ts">
import { supabase } from "@/supabase";
import { ref } from "@vue/reactivity";

import { label } from "@formkit/inputs";
import { useRouter } from "vue-router";
import Card from "./card.vue";

const router = useRouter();
const Maisons = ref({});

const props = defineProps(["id"]);
if (props.id) {
  // On charge les données de la maison
  let { data, error } = await supabase
    .from("Maison")
    .select("*")
    .eq("id", props.id);
  if (error) console.log("n'a pas pu charger le table Maison :", error);
  else Maisons.value = (data as any[])[0];
}

async function upsertMaison(dataForm, node) {
  const { data, error } = await supabase.from("Maisons").upsert(dataForm);
  if (error || !data) node.setErrors([error?.message]);
  else {
    node.setErrors([]);
    router.push({ name: "edit-id", params: { id: data[0].id } });
  }
}

const { data: dataQuartierCommune, error } = await supabase
  .from("quartiercommune")
  .select("*");
if (error) console.log("n'a pas pu charger la vue quartiercommune :", error);

</script>

<template>
  <div class="flex flex-wrap justify-center">
    <div class="p-2">
      <h2 class="text-2xl">Résultat (Prévisualition )</h2>
      <Card v-bind="Maisons" />
    </div>
    <div
      class="flex items-center rounded-xl border-x-2 border-y-8 border-current border-x-white border-y-black bg-indigo-500 text-center font-medium"
    >
      <div class="m-4 p-4">
        <!--on passe la ref a fromkit -->

        <FormKit
          type="form"
          @submit="upsertMaison"
          v-model="Maisons"
          :submit-attrs="{
            classes: {
              input:
                'bg-pink-600 text-white p-1 rounded hover:bg-white hover:text-black',
            },
          }"
          :config="{
            classes: {
              input:
                'p-1 rounded  border-x-2 border-y-2 border-x-black border-y-black focus:bg-green-300 focus:border-x-white focus:border-current focus:border-y-white focus:border-y-4 focus:border-x-4 hover:bg-red-400 ',
              label: 'text-black',
            },
          }"
        >
          <FormKit name="nom" label="Nom" />
          <FormKit name="prix" label="Prix" type="number" />
          <FormKit name="lieux" label="Lieux" />
          <FormKit name="bed" label="Bed" type="number" />
          <FormKit name="bathroom" label="Bathroom" type="number" />
          <FormKit name="space1" label="Space" type="number" />
          <FormKit name="quartier" label="quartier" type="text" />
          <FormKit name="commune" label="commune" type="text" />

          

          <FormKit
            name="favori"
            label="Mettre en valeur "
            type="checkbox"
            wrapper-class="flex"
            class="p-7"
          />
        </FormKit>
      </div>
    </div>
  </div>
</template>
