<script setup lang="ts">

import { supabase } from "../supabase";
import { ref } from "@vue/reactivity"
import Card from "../components/card.vue";

console.log("supabase :", supabase); // pour vérifier et "garder" supabase dans le code

const maisons = [supabase]; // à remplacer par l'appel à Supabase

let { data: Maison, error } = await supabase
    .from('Maison')
    .select('*')

console.log("Maison : ", Maison);

const user = ref(supabase.auth.user());

supabase.auth.onAuthStateChange(() => {
    user.value = supabase.auth.user()
})

</script>
        
    
<template>
    <div class="flex items-center flex-col">
        <h6>Liste supabase</h6>
        <div v-for ="Maisons in Maison" :key="Maisons.nom">
            <Card v-bind="Maisons"></Card>
        </div>
    </div>
</template>
