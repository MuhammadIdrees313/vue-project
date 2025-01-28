<template>
   
   <div class="flex flex-col p-8">
    <input type="text" class="rounded border-3 border-gray-300 w-full"  placeholder=" Search for Meals"/>
    <div class="flex gap-4 justify-center m-2">
      <router-link :to="{name:'byLetter', params: {letter}}" v-for="letter of letters" :key="letter">
      {{ letter }}
    </router-link>

    </div>
   </div>
</template>
<script>
import { onMounted } from 'vue';
import axiosClient from '../axiosClient.js';

export default {
  setup() {
    const letters = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'.split("");

    onMounted(async () => {
      try {
        const response = await axiosClient.get('list.php?i=list');
        console.log(response.data);
      } catch (error) {
        console.error('Error fetching data:', error);
      }
    });

    return { letters };
  },
};
</script>
