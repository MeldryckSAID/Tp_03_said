<script setup lang="ts">
import Bed from "../components/icons/bed.vue";
import Bath from "../components/icons/bath.vue";
import Space from "../components/icons/space.vue";

defineProps({
  nom: { type: String, default: "remire" },
  prix: { type: Number, default: "2700" },
  lieux: { type: String, default: "montjoly 45 rue route des plages 97354" },
  bed: { type: Number, default: 4 },
  bathroom: { type: Number, default: 2 },
  space1: { type: String, default: "12*90" },
  Image: { type: String, default: "src/assets/house.png" },
});
</script>

<template>
  <figure
    class="mx-8 mt-12 flex flex-col rounded-lg border-x-2 w-max border-y-4 border-indigo-400"
  >
    <img
      src="src/assets/house2.png"
      alt="house"
      class="h-48 w-full rounded-t-lg object-cover"
    />
    <figcaption
      class="flex w-full flex-col gap-4 rounded-b border border-x-4 border-y-4 border-indigo-50 py-7 px-5"
    >
      <div class="flex justify-between">
        <div class="w-2/5">
          <div class="flex items-center">
            <p class="text-2xl font-bold text-indigo-500"></p>
            <span class="text-xs font-normal text-gray-900"
              >{{ prix }} $/month</span
            >
          </div>
          <p class="text-2xl font-bold">{{ nom }}</p>
        </div>
        <div
          class="flex h-12 w-12 items-center justify-center rounded-full border-2 border-indigo-100"
        >
          <HeartIcon class="h-6 stroke-indigo-500 text-transparent"></HeartIcon>
        </div>
      </div>
      <p class="text-base font-normal text-gray-900">
        {{ lieux }}
      </p>
      <div class="w-full border border-indigo-50"></div>
      <div class="flex justify-between">
        <div class="flex items-center gap-2">
          <bed class="h-5 stroke-indigo-500"></bed>
          <span class="text-xs text-gray-500">{{ bed }} Beds</span>
        </div>
        <div class="flex items-center gap-2">
          <bath class="h-5 stroke-indigo-500"></bath>
          <span class="text-xs text-gray-500">{{ bathroom }} Bathrooms</span>
        </div>
        <div class="flex items-center gap-2">
          <space1 class="h-5 stroke-indigo-500"></space1>
          <span class="text-xs text-gray-500">{{ space1 }} m²</span>
        </div>
      </div>
    </figcaption>
  </figure>
</template>
