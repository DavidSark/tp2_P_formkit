<script setup lang="ts">
import { ref } from "@vue/reactivity";
import card from "@/components/card.vue";
import { label } from "@formkit/inputs";

const maison = ref({});

</script>


<template>
    <div class="flex flex-row-reverse justify-center">
        <div class="p-2">
            <h2 class="text-2xl">Résultat (Prévisualisation)</h2>
            <card v-bind="maison"/>
        </div>
        <div class="p-2 border-2 mt-20 bg-indigo-50 rounded-2xl">
            <div class="p-4 ">
                <FormKit type="form" v-model="maison" :config="{
                    classes: {
                    input: 'p-1 rounded border-gray-300 mb-3 shadow-sm border',
                    label: 'text-gray-600 font-medium',
                    },
                    }" :submit-attrs="{ classes: 
                        { input: 'border-2 bg-indigo-200 border-indigo-200 p-1 rounded ',
                          label:''
                     } }">
                    <FormKit name="name" label="Nom" />
                    <FormKit name="adresse" label="Adresse" />
                    <FormKit name="bed" label="Nombre de lits" type="number"/>
                    <FormKit name="bathroom" label="Nombre de salle de bain" type="number"/>
                    <FormKit name="mcarre" label="Superficie en m²" type="number"/>
                    <FormKit name="price" label="Prix" type="number"/>
                    <FormKit name="fav" label="Ajouter l'offre aux favoris" type="checkbox" wrapper-class="flex"
    /> 
                </FormKit>
            </div>
        </div>
    </div>
</template>