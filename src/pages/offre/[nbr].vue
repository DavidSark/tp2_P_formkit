<script setup lang="ts">
    import Maisons from '../../assets/Maisons.json'
    import Card from '../../components/card.vue'
    
    defineProps({
        nbr: String,
    })
</script>

<template>
    <div>
        <h1>{{nbr}}</h1>
        <Card :price="Maisons[nbr].price"
              :image="Maisons[nbr].image"
              :name="Maisons[nbr].name"
              :adresse="Maisons[nbr].adresse"
              />
    </div>
</template>