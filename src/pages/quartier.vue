<script setup lang="ts">
import { supabase } from "../supabase";
import groupBy from "lodash/groupBy";
import { Disclosure, DisclosureButton, DisclosurePanel } from "@headlessui/vue";

const { data, error } = await supabase.from("quartiercommune").select("*");

if (error) console.log("n'a pas pu charger la table quartiercommune :", error);
</script>

<template>
  <h3 class="bg-black py-4 text-center text-xl font-bold text-indigo-400">
    Liste des quartier par commune avec supabase
  </h3>

  <section class="flex flex-col bg-indigo-300 p-4 font-bold text-white">
    <!-- <ul>
      <li v-for="quartierObject in (data as any[])">
        {{ quartierObject.libelle_commune }} -
        {{ quartierObject.libelle_quartier }}
      </li>
    </ul> -->

    <Disclosure
      v-for="(tableauDeQuartieDUneCommune, libelle_commune) in groupBy(
        data,
        'libelle_commune'
      )"
      :key="libelle_commune"
    >
      <DisclosureButton>
        {{ libelle_commune }}
      </DisclosureButton>
      <DisclosurePanel class="text-black mx-4 list-item font-normal">
        <ul>
          <li
            v-for="{
              code_quartier,
              libelle_quartier,
            } in tableauDeQuartieDUneCommune"
           
            :key="code_quartier"
          >
            {{ libelle_quartier }}
          </li>
        </ul>
      </DisclosurePanel>
    </Disclosure>
  </section>
</template>
