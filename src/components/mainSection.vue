<script setup>
  import { ref } from 'vue';
  import CurrentNotes from './CurrentNotes.vue';


</script>

<template>
  <div class='section-main-container'>
    <CurrentNotes > </CurrentNotes>
  </div>

</template>



<style scoped>

  .section-main-container{
    display: flex;
    min-height: 85vh;
    }
</style>
