<script setup lang="ts">
import card from "@/components/card.vue";
import { label } from "@formkit/inputs";
import { useRouter } from "vue-router";
import { ref } from "@vue/reactivity";
import { supabase } from "@/supabase";

    const router = useRouter();
    const quartier = ref({});
    
    const props = defineProps(["id"]);
if (props.id) {
    // On charge les données de la maison
    let { data, error } = await supabase
        .from("Quartier")
        .select("*")
        .eq("code_Quartier", props.id);
    if (error) console.log("n'a pas pu charger le table Quartier :", error);
    else quartier.value = (data as any[])[0];
}

async function modifQuartier(dataForm, node) {
    const { data, error } = await supabase.from("Quartier").upsert(dataForm);
    if (error || !data) node.setErrors([error?.message])
    else {
        node.setErrors([]);
        router.push({ name: "edit-id", params: { id: data[0].id } });
    }
}

const { data: listeCommune, error } = await supabase
  .from("Commune")
  .select("*");
if (error) console.log("n'a pas pu charger la table Commune :", error);
// Les convertir par `map` en un tableau d'objets {value, label} pour FormKit
const optionsCommune = listeCommune?.map((commune) => ({
  value: commune.code_Commune,
  label: commune.libelle_Commune,
}));

    </script>
    <template>
      <div>
        <div class="flex flex-row-reverse justify-center">
          <div class="p-2">
            <h2 class="text-2xl"> (Prévisualisation)</h2>
            <!-- <card v-bind="quartier" /> -->
        </div>
          <FormKit @submit="modifQuartier" type="form" v-model="quartier" :config="{
                classes: {
                input: 'p-1 rounded border-gray-300 mb-3 shadow-sm border',
                label: 'text-gray-600 font-medium',
                },
                }" :submit-attrs="{ classes: 
                       { input: 'border-2 bg-indigo-200 border-indigo-200 p-1 rounded ',
                         label:''
                    } }">
        <FormKit class="border-2 borcer" name="libelle_Quartier" label="Nom" />

        <FormKit
        type="select"
        name="code_Commune"
        label="Commune"
        :options="optionsCommune"
      />
        
      </FormKit>
        </div>
      </div>
     
    </template>