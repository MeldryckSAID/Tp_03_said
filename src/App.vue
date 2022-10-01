<template>
  <nav>
    <h4 class="text-xl">
      <Bars3Icon class="inline-block h-5 w-5 text-blue-500" />
      menu (dans <code class="font-mono">/src/App.vue</code>)
    </h4>
    <ul>
      <li>
        <router-link class="text-black underline" to="/">
          <code class="font-mono">/src/pages/index.vue</code>
        </router-link>
      </li>
      <p>tp1</p>
      <li>
        <router-link class="text-green-600 underline" to="Simple">
          <code class="font-mono">/src/pages/Simple.vue</code>
        </router-link>
      </li>
      <li>
        <router-link class="text-pink-600 underline" to="liste">
          <code class="font-mono">/src/pages/liste.vue</code>
        </router-link>
      </li>
      <li>
        <router-link class="text-green-700 underline" to="list-fetch">
          <code class="font-mono">liste-fetch.vue</code>
        </router-link>
      </li>
      <p>tp3</p>

      <li>
        <router-link class="text-zinc-900-700 underline" to="new">
          <code class="font-mono">/src/pages/new.vue</code>
        </router-link>
      </li>

      <li>
        <router-link class="text-purple-700 underline" to="list-supabase">
          liste depuis supa
        </router-link>
      </li>
      <li>
        <router-link class="text-violet-700 underline" to="seco">
          lien pour se connecter
        </router-link>
      </li>

      <hr />
      <p>tp4</p>
      <hr />
      <li>
        <router-link class="text-violet-700 underline" to="quartier">
          afficher les Quartiers
        </router-link>
      </li>
      <li>
        <router-link class="text-violet-700 underline" to="editQuartier">
          editer les Quartiers
        </router-link>
      </li>
    </ul>
  </nav>

  <!-- Affiche les pages -->
  <Suspense>
    <router-view class="m-2 border-2 p-2" />
    <template #fallback> Loading... </template>
  </Suspense>
</template>

<script setup lang="ts">
import { Bars3Icon } from "@heroicons/vue/20/solid";
</script>
