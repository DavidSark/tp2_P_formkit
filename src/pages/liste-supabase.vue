<script setup lang="ts">

import { supabase } from "../supabase";
import {ref} from "@vue/reactivity"
import FormulaireOffreMaison from "../components/FormulaireOffreMaison.vue";

console.log("supabase :", supabase); // pour vérifier et "garder" supabase dans le code

const maisons = [supabase]; // à remplacer par l'appel à Supabase
  
let { data: Maison, error } = await supabase
  .from('Maison')
  .select('*')

  console.log("Maison : ", Maison);

 const user = ref(supabase.auth.user());

supabase.auth.onAuthStateChange(()=>{
 user.value = supabase.auth.user()
})

</script>
        
    
<template>
    <div>
        <h6>Liste supabase</h6>
        <FormulaireOffreMaison/>
    </div>
</template>
