
<script setup lang="ts">

import FormulaireOffreMaison from "../../components/FormulaireOffreMaison.vue";
defineProps({
        id: String,
    })
</script>

<template>
    <div>
        <p>Edit</p>
        <FormulaireOffreMaison :id="id" />
    </div>
 
</template>