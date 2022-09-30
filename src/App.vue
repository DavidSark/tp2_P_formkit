<template>
  <nav>
                <div class="hidden lg:flex justify-center bg-indigo-200 space-x-12">
                    <div class="flex items-center py-5 px-2">
                        <RouterLink to="/"><img src="public/favicon.ico"></RouterLink>
                    </div>

                    <div class=" hidden text-black lg:flex items-center space-x-6">
                        <router-link class="text-black no-underline hover:text-indigo-400" to="/">
                          <code class="font-mono">Accueil</code>
                        </router-link>
                        <router-link class="text-black no-underline hover:text-indigo-400" to="/simple">
                          <code class="font-mono">Simple.vue</code>
                        </router-link>
                        <router-link class="text-black  no-underline hover:text-indigo-700" to="/liste">
                          <code class="font-mono">Liste.vue</code>
                        </router-link>
                        <router-link class="text-black  no-underline hover:text-indigo-400" to="/liste-fetch">
                          <code class="font-mono">Liste-Fetch</code>
                        </router-link>
                        <!-- <router-link class="text-black  no-underline hover:text-indigo-400" to="/offre/1">
                          <code class="font-mono">Offre nbr1</code>
                        </router-link>
                        <router-link class="text-black  no-underline hover:text-indigo-400" to="/offre/2">
                          <code class="font-mono">Offre nbr2</code>
                        </router-link>  -->
                        <router-link class="text-black  no-underline hover:text-indigo-400" to="/edit/new">
                          <code class="font-mono">New.vue</code>
                        </router-link>
                        <router-link class="text-black  no-underline hover:text-indigo-400" to="/liste-supabase">
                          <code class="font-mono">Liste-Supabase</code>
                        </router-link>
                        <router-link class="text-black  no-underline hover:text-indigo-400" to="/authentification">
                          <code class="font-mono">Authentification</code>
                        </router-link>
                        <router-link class="text-black  no-underline hover:text-indigo-400" to="/edit/id ">
                          <code class="font-mono">Edit</code>
                        </router-link>
                        <router-link class="text-black  no-underline hover:text-indigo-400" to="/quartier">
                          <code class="font-mono">Quartier</code>
                        </router-link>
                        <router-link class="text-black  no-underline hover:text-indigo-400" to="/quartier/new">
                          <code class="font-mono">New Quartier</code>
                        </router-link>
                    </div>
                </div>
              
       <!--Menu responsive-->
    <div class="lg:hidden flex items-center">
                    <button v-on:click="menuVisible = !menuVisible " class=""> 
                        <svg xmlns="http://www.w3.org/2000/svg" class="h-8 w-8 text-black" 
                        viewBox="0 0 20 20" fill="currentColor" :class="{hidden: !menuVisible}">
                        <path fill-rule="evenodd" d="M3 5a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1zM3 10a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1zM3 15a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1z" clip-rule="evenodd" />
                        </svg>
                    </button>        
     </div>

                <div class="" :class="{hidden: menuVisible }">
            <button v-if="!menuVisible" v-on:click="menuVisible = !menuVisible" class="" >
                      <svg xmlns="http://www.w3.org/2000/svg" class="h-8 w-8 text-black" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                      <path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12" />
                      </svg>
            </button>
            <h4 class="text-xl">
      <Bars3Icon class="inline-block h-5 w-5 text-blue-500" />
      Naviguer à travers le menu
    </h4>
    <ul class="ml-8">
      <li>
        <router-link class="text-black no-underline hover:text-indigo-400" to="/">
          <code class="font-mono">Accueil</code>
        </router-link>
      </li>
      <li>
        <router-link class="text-black no-underline hover:text-indigo-400" to="/simple">
          
          <code class="font-mono">Simple.vue</code>
        </router-link>
      </li>
      <li>
        <router-link class="text-black  no-underline hover:text-indigo-700" to="/liste">
          <code class="font-mono">Liste.vue</code>
        </router-link>
      </li>
      <li>
        <router-link class="text-black  no-underline hover:text-indigo-400" to="/liste-fetch">
          <code class="font-mono">Liste-Fetch</code>
        </router-link>
      </li>
      <li>
        <router-link class="text-black  no-underline hover:text-indigo-400" to="/offre/1">
          <code class="font-mono">Offre nbr1</code>
        </router-link>
      </li>
      <li>
        <router-link class="text-black  no-underline hover:text-indigo-400" to="/offre/2">
          <code class="font-mono">Offre nbr2</code>
        </router-link>
      </li>
      <li>
        <router-link class="text-black  no-underline hover:text-indigo-400" to="/edit/new">
          <code class="font-mono">New.vue</code>
        </router-link>
      </li>

      <li>
        <router-link class="text-black  no-underline hover:text-indigo-400" to="/liste-supabase">
          <code class="font-mono">Liste-Supabase</code>
        </router-link>
      </li>

      <li>
        <router-link class="text-black  no-underline hover:text-indigo-400" to="/authentification">
          <code class="font-mono">Authentification</code>
        </router-link>
      </li>
      <li>
        <router-link class="text-black  no-underline hover:text-indigo-400" to="/edit/id ">
          <code class="font-mono">Edit</code>
        </router-link>
      </li>

    </ul>
          </div>
  </nav>

  <!-- Affiche les pages -->
  <Suspense>
    <router-view class="m-2 border-2 p-2" />
    <template #fallback>
      Loading...
    </template>
  </Suspense>
</template>

<script setup>
import {ref} from 'vue';
const menuVisible = ref(true);
</script>



