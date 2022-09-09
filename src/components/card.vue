<template>
     <figure class="flex flex-col mt-12 mx-8">
    <img
      src="src/assets/house2.png"
      alt="house"
      class="rounded-t-lg w-full h-48 object-cover"
    />
    <figcaption
      class="
        flex
        w-full
        flex-col
        gap-4
        rounded-b
        border border-indigo-50
        py-7
        px-5
      "
    >
      <div class="flex justify-between">
        <div class="w-2/5">
          <div class="flex items-center">
            <p class="text-2xl font-bold text-indigo-500">$4800</p>
            <span class="text-xs font-normal text-gray-900">/month</span>
          </div>
          <p class="text-2xl font-bold">Tarpon Bay</p>
        </div>
        <div
          class="
            flex
            h-12
            w-12
            items-center
            justify-center
            rounded-full
            border-2 border-indigo-100
          "
        >
          <HeartIcon class="h-6 stroke-indigo-500 text-transparent"></HeartIcon>
        </div>
      </div>
      <p class="text-base font-normal text-gray-900">
        103 Lake Shores, Michigan, IN
      </p>
      <div class="w-full border border-indigo-50"></div>
      <div class="flex justify-between">
        <div class="flex items-center gap-2">
          <bed class="h-5 stroke-indigo-500"></bed>
          <span class="text-xs text-gray-500">4 Beds</span>
        </div>
        <div class="flex items-center gap-2">
          <bath class="h-5 stroke-indigo-500"></bath>
          <span class="text-xs text-gray-500">2 Bathrooms</span>
        </div>
        <div class="flex items-center gap-2">
          <mcarre class="h-5 stroke-indigo-500"></mcarre>
          <span class="text-xs text-gray-500">6x7.5 m²</span>
        </div>
      </div>
    </figcaption>
  </figure>

  
</template>

<script>
import bed from "../components/icons/bed.vue";
import bath from "../components/icons/bath.vue";
import mcarre from "../components/icons/mcarre.vue";

export default {
  name: "App",
  components: {
    bed,
    bath,
    mcarre,
  },
}

</script>
