<script setup lang="ts">
    import Maisons from '../../assets/Maisons.json'
    import Card from '../../components/card.vue'
    
    defineProps({
        id: String,
    })
</script>

<template>
    <div class="flex items-center flex-col">
        <h1>{{id}}</h1>
        <Card :price="Maisons[id].price"
              :image="Maisons[id].image"
              :name="Maisons[id].name"
              :adresse="Maisons[id].adresse"
              />
    </div>
</template>