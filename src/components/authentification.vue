<script setup lang="ts">
import { ref } from "@vue/reactivity";
import { supabase, user } from "@/supabase";

async function signIn(data, node) {
  const { user, error } = await (nvlUtilisateur.value
    ? supabase.auth.signUp(data)
    : supabase.auth.signIn(data));
  if (error) {
    console.error(error);
    node.setErrors([error.message]);
  }
}
const nvlUtilisateur = ref(false);
</script>

<template>
  
  <div class="flex justify-center bg-indigo-300">
    <button  class="bg-red-700 hover:text-white m-4 p-6 text-xl font-bold rounded-full" v-if="user" @pointerdown="supabase.auth.signOut( ) ">
      Se déconnecter ({{ user.email }})
    </button>
    <FormKit
      v-else
      type="form"
      :submit-attrs="{
        classes: {
          input:
            'bg-white  m-4 p-4 rounded hover:bg-black hover:text-indigo-300',
        },
      }"
      :submit-label="nvlUtilisateur ? 'S\'inscrire' : 'Se connecter'"
      @submit="signIn"
    >
      <FormKit name="email" label="Votre eMail" type="email" />
      <FormKit name="password" label="Mot de passe" type="password" />
      <formKit
        label="Nouvel utilisateur ?"
        class="flex flex-row"
        name="nvlUtilisateur"
        type="checkbox"
        v-model="nvlUtilisateur"
      />
    </FormKit>
  </div>
</template>
