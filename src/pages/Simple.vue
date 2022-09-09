<script setup lang="ts">
import card from "../components/card.vue";

 const proprietes = defineProps({
  name : {type: String, default:'Tarpon Bat'    },
  prix: {type:Number, default:'4800'      },
  adresse: {type: String, default: '103 Lake Shores, Michigan, IN'       },
  bed: {type:Number , default: 4           },
  bathroom: {type:Number , default: 2           },
  mcarr: {type:String , default: '6x7.5'           },
  
    });

  /*  prix: Number,   
    nom: String,
    adresse: String,
    bed: String,
    bathroom: String,
    mcarre: Number,
*/

</script>

<template>
    <div>
        <p>Simple</p>
        <card></card>
    </div>
</template>
