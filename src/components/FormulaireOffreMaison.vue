<script setup lang="ts">
    import{ ref } from "@vue/reactivity";
    import Card from "./card.vue";
    //on fait une variable réative qui référence les données 
    //attention : faire une ref pas une re&ctive car :
    //c'est l'objet qui doit etre réactif pas ses props 
    const Maisons = ref({});
</script>

<template>
    
    <div class="flex flex-wrap">
        <div class= " p-2">
            <h2 class="text-2xl"> Résultat (Prévisualition )</h2>
            <Card v-bind="Maisons"/>
        </div>
         <div class="justify-center  border-x-2  border-x-blue-900 border-y-2  border-y-blue-900 text-center ">
        <div class="p-2">
            <!--on passe la ref a fromkit -->
            <FormKit type="form" v-model="Maisons"
            :submit-attrs="{ classes: { input: 'bg-red-300 p-1 rounded' } }"

            :config="{
                     classes: {
                     input: 'p-1 rounded  border-x-2 border-y-2 border-x-black border-y-black  ',
                     label: 'text-black',
                     
 },
 }"
            >
                <FormKit name="nom" label="Nom"/>
                <FormKit name="prix" label="Prix" type="number"/>
                <FormKit name="favori" label="Mettre en valeur " type="checkbox" wrapper-class="flex" class="p-7" />
               

            </FormKit>
        </div>
        </div> 
    </div>
    
</template>