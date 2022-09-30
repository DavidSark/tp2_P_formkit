<script setup lang="ts">
import groupBy from "lodash/groupBy";
import {Disclosure} from "@headlessui/vue";
import { supabase } from "../../supabase";
const { data, error } = await supabase.from("quartiercommune").select("*");
if (error) console.log("n'a pas pu charger la table quartiercommune :", error);
//console.log(eval(await (await fetch("https://cdn.jsdelivr.net/npm/lodash@4.17.21/lodash.min.js")).text()))
</script>

<template>
  <section class="flex flex-col">
    <h3 class="text-2xl">Liste des quartiers</h3>
    <!-- <ul>
      <li v-for="quartiercommune in (data as any[])">
        {{ quartiercommune.libelle_Commune }} -
        {{ quartiercommune.libelle_Quartier }}
      </li>
    </ul> -->
    
    <Disclosure
    v-for="(listeQuartier, libelle_Commune) in groupBy(
      data,
      'libelle_Commune'
    )"
    :key="libelle_Commune"
    >
    <DisclosureButton  v-for="c in (listeQuartier as any[])" :key="c.libelle_Commune"
                class="border">
        {{ c.libelle_Commune }}
    </DisclosureButton>

    <DisclosurePanel  v-for="q in (listeQuartier as any[])" :key="q.libelle_Quartier">
        {{ q.libelle_Quartier }}
    </DisclosurePanel>
    </Disclosure>
  </section>
</template>