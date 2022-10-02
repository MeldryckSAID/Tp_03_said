<script setup lang="ts">
import { supabase } from "@/supabase";
import { ref } from "@vue/reactivity";

import { label } from "@formkit/inputs";
import { useRouter } from "vue-router";
import Card from "./card.vue";

const router = useRouter();
const quartier = ref({});

const { data: libelle_commune, error } = await supabase
  .from("commune")
  .select("*");
if (error) console.log("n'a pas pu charger la table Commune :", error);


//test

// Les convertir par `map` en un tableau d'objets {value, label} pour FormKit
const optionsCommune = libelle_commune?.map((commune) => ({
  value: commune.code_Commune,
  label: commune.libelle_commune,
}));

const props = defineProps(["id"]);
if (props.id) {
  // On charge les données de la maison
  let { data, error } = await supabase
    .from("quartier")
    .select("*")
    .eq("id", props.id);
  if (error) console.log("n'a pas pu charger le table quartier :", error);
  else quartier.value = (data as any[])[0];
}



async function upsertquartier(dataForm, node) {
  const { data, error } = await supabase.from("quartier").upsert(dataForm);
  if (error || !data) node.setErrors([error?.message]);
  else {
    node.setErrors([]);
    router.push({ name: "edit-id", params: { id: data[0].id } });
  }
}

async function supprimerQuartier() {
  const { data, error } = await supabase
    .from("quartier")
    .delete()
    .match({ code_quartier: quartier.value.code_quartier });
  if (error) {
    console.error(
      "Erreur à la suppression de ",
      quartier.value,
      "erreur :",
      error
    );
  } else {
    router.push("/quartier");
  }
}
</script>

<template>
  <div class="flex flex-wrap justify-center">
    <div class="p-2">
      <Card v-bind="quartier" />
    </div>
    <div
      class="flex items-center rounded-xl border-x-2 border-y-8 border-current border-x-white border-y-black bg-indigo-500 text-center font-medium"
    >
      <div class="m-4 p-4">
        <!--on passe la ref a fromkit -->

        <FormKit
          type="form"
          @submit="upsertquartier"
          v-model="quartier"
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
          <FormKit
            class="p-7"
            name="libelle_quartier"
            label="quartier"
            type="text"
          />

          <FormKit
            name="favori"
            label="Mettre en valeur "
            type="checkbox"
            wrapper-class="flex"
            class="p-7"
          />
        </FormKit>
        
        <FormKit
          type="select"
          name="code_Commune"
          label="commune"
          :options="optionsCommune"
        />
        <dialog>Sup </dialog>

        <button
          type="button"
          v-if="quartier.code_quartier"
          @click="($refs.dialogSupprimer as any).showModal()"
          class="focus-style justify-self-end rounded-md bg-red-500 p-2 shadow-sm"
        >
          Supprimer l'offre
        </button>
        <dialog
          ref="dialogSupprimer"
          @click="($event.currentTarget as any).close()"
        >
          <button
            type="button"
            class="focus-style justify-self-end rounded-md bg-blue-300 p-2 shadow-sm"
          >
            Annuler</button
          ><button
            type="button"
            @click="supprimerQuartier()"
            class="focus-style rounded-md bg-red-500 p-2 shadow-sm"
          >
            Confirmer suppression
          </button>
        </dialog>
      </div>
    </div>
  </div>
</template>
