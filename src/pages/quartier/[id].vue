<script setup lang="ts">
    import FormulaireQuartier from "../../components/FormulaireQuartier.vue";

    defineProps({
        id: String,
    })

    </script>
    <template>
      <div class="p-2">
        <FormulaireQuartier :id = "id" />
      </div>
    </template>