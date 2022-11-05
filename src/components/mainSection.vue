<script setup>
  import { ref } from 'vue';
  import CurrentNotes from './subComponents/CurrentNotes.vue';
  import Doing from './Doing.vue'

  // Create an array to store the archive notes
  let archivegNoteList = ref([]);

</script>

<template>

  <div class='section-main-container'>
    <CurrentNotes > </CurrentNotes>
  </div>

</template>



<style scoped>
  .section-main-container{
  background-color: green;
  display: flex;
  min-height: 85vh;
  }

</style>
