<script setup lang="ts">
import Card from "../components/card.vue";



const unObjet = {
    price: "100 800", 
    name: "Random",
    adresse: "Je sais pas ou",
    bed: 7,
    bathroom: "4",
    mcarre: "99"

}
  /*  
    defineProps({
      name : {type: String, default:'Tarpon Bat'                                },
      price: {type:Number, default:'4800'                                        },
      adresse: {type: String, default: '103 Lake Shores, Michigan, IN'          },
      bed: {type:Number , default: 8                                           },
      bathroom: {type:Number , default: 2                                       },
      mcarre: {type:String , default: '6x7.5'                                    },
      });
*/

</script>

<template>
    <div>
        <p>Simple</p>
        <Card></Card>
        <Card v-bind="{name: 'oopsiz', price:'300 000', adresse:'Une bonne adresse', bed:'8', bathroom: '3', mcarre:'87'}"></Card>
        <Card v-bind="unObjet"></Card>
    </div>
</template>
