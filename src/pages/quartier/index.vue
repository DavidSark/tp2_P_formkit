<script setup lang="ts">
import { supabase } from "../../supabase";
const { data, error } = await supabase.from("quartiercommune").select("*");
if (error) console.log("n'a pas pu charger la table quartiercommune :", error);
//console.log(eval(await (await fetch("https://cdn.jsdelivr.net/npm/lodash@4.17.21/lodash.min.js")).text()))
</script>

<template>
  <section class="flex flex-col">
    <h3 class="text-2xl">Liste des quartiers</h3>
    <ul>
      <li v-for="quartiercommune in (data as any[])">
        {{ quartiercommune.libelle_Commune }} -
        {{ quartiercommune.libelle_Quartier }}
      </li>
    </ul>
    
  </section>
</template>