<script setup lang="ts">
import Card from "../components/card.vue";



const unObjet = {
    price: "12 800", 
    name: "Los Angeles",
    adresse: "122 Elm Street",
    bed: 7,
    bathroom: "4",
    mcarre: "69"

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
        <Card v-bind="{name: 'France', price:'2 000', adresse:'Montbéliard', bed:'8', bathroom: '3', mcarre:'37'}"></Card>
        <Card v-bind="unObjet"></Card>
    </div>
</template>
