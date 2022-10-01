<script setup lang="ts">
import { supabase } from "../supabase";
import groupBy from "lodash/groupBy";
import { Disclosure, DisclosureButton, DisclosurePanel } from "@headlessui/vue";

const { data, error } = await supabase.from("quartiercommune").select("*");

if (error) console.log("n'a pas pu charger la table quartiercommune :", error);
</script>

<template>
  <section class="flex flex-col">
    <h3 class="text-2xl">Liste des quartier par commune avec supabase</h3>

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
      <DisclosurePanel>
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
