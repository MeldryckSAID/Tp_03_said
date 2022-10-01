<template >
  <nav class="bg-black p-8">
    <ul class="box-border flex flex-row justify-around   text-white">
      <li class="m-6">
        <div
          class="font-mono text-white hover:stroke-indigo-300 hover:text-indigo-300"
        >
          <router-link to="/">
            <HomeIcon class="hover:fill-transparent" />
            <h3>Home</h3>
          </router-link>
        </div>
      </li>

      <ul class=" list-decimal ">
        <h4 class="text-xl text-center ">Tp1</h4>
         <li class="my-3 hover:text-indigo-300">
          <router-link class="underline" to="Simple">
            <code class="font-mono">Liste Simple</code>
          </router-link>
        </li>
         <li class="my-3 hover:text-indigo-300">
          <router-link class="file: underline" to="liste">
            <code class="font-mono">Liste</code>
          </router-link>
        </li>
         <li class="my-3 hover:text-indigo-300">
          <router-link class="underline" to="list-fetch">
            <code class="font-mono">Liste-fetch</code>
          </router-link>
        </li>
      </ul>

      <ul class=" list-decimal">
        <h4 class="text-xl text-center ">Tp3</h4>

         <li class="my-3 hover:text-indigo-300">
          <router-link class="text-zinc-900-700 underline" to="new">
            <code class="font-mono">Nouvelle Annonce</code>
          </router-link>
        </li>

         <li class="my-3 hover:text-indigo-300">
          <router-link class="underline" to="list-supabase">
            liste depuis Supabase
          </router-link>
        </li>
         <li class="my-3 hover:text-indigo-300">
          <router-link class="underline" to="seco">
            Connectez vous
          </router-link>
        </li>
      </ul>

      <ul class=" list-decimal my-3" >
        <h4 class="text-xl text-center ">Tp4</h4>

        <li class="my-3 hover:text-indigo-300">
          <router-link class="underline" to="quartier">
            Nos Quartiers
          </router-link>
        </li>

         <li class="my-3 hover:text-indigo-300">
          <router-link class="underline" to="editQuartier">
            Editer de nouveaux Quartiers
          </router-link>
        </li>
         <li class="my-3 hover:text-indigo-300">
          <router-link class="underline" to="suppression">
            Supprimer les Quartiers
          </router-link>
        </li>
      </ul>
    </ul>
  </nav>

  <!-- Affiche les pages -->
  <Suspense>
    <router-view class="m-2 border-2 p-2" />
    <template #fallback > Loading... </template>
  </Suspense>
</template>

<script setup lang="ts">
import { HomeIcon } from "@heroicons/vue/20/solid";
</script>
