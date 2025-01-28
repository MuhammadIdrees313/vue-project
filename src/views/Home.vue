<template>
   
   <div class="flex flex-col p-8">
    <input type="text" class="rounded border-3 border-gray-300 w-full"  placeholder=" Search for Meals"/>
    <div class="flex gap-4 justify-center m-2">
      <router-link to="/" v-for="letter of letters" :key="letter">
      {{ letter }}
    </router-link>

    </div>
   </div>
</template>
<script>
import { computed } from 'vue';
import store from '../store';

export default {
  setup() {
    const meals = computed(() => store.state.meals);
    const letters = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'.split("");
    return { meals , letters}; 
  },
};
</script>
