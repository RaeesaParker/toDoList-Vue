<script setup>
  import { ref } from 'vue';
  import CurrentNotes from './subComponents/CurrentNotes.vue';

  // Create array to store current note list 
  let currentNoteList = ref([]);

</script>

<template>

  <div class='section-main-container'>
     <CurrentNotes currentNoteList= {currentNoteList} > </CurrentNotes>
  </div>
  
</template>



<style scoped>
  .section-main-container{
  /* background-color: green; */
  display: flex;
  min-height: 85vh;
  }
</style>
