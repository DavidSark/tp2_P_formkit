<script setup lang="ts">
import { label } from "@formkit/inputs";
import { useRouter } from "vue-router";
import { ref } from "@vue/reactivity";
import { supabase } from "@/supabase";
const { data, error } = await supabase.from("quartiercommune").select("*");
if (error) console.log("n'a pas pu charger la table quartiercommune :", error);
    defineProps<{
      id: string;
    }>();
    // TODO

    const router = useRouter();
    const quartier = ref({});
    
    async function upsertQuartier(dataForm, node) {
    const { data, error } = await supabase.from("Quartier").upsert(dataForm);
    if (error || !data) node.setErrors([error?.message])
    else {
        node.setErrors([]);
        router.push({ name: "edit-id", params: { id: data[0].id } });
    }
}
    </script>
    <template>
      <div>
        <div>
          <FormKit @submit="upsertQuartier" type="form" v-model="quartier" :config="{
                classes: {
                input: 'p-1 rounded border-gray-300 mb-3 shadow-sm border',
                label: 'text-gray-600 font-medium',
                },
                }" :submit-attrs="{ classes: 
                       { input: 'border-2 bg-indigo-200 border-indigo-200 p-1 rounded ',
                         label:''
                    } }">
        <FormKit class="border-2 borcer" name="libelle_Quartier" label="Nom" />

       
        
      </FormKit>
        </div>
      </div>
     
    </template>