<script setup>
  import { ref } from 'vue';
  import CreateNote from './CreateNote.vue';



</script>

<template>
  <div class="section-insert">
  <CreateNote title="Hello" body="something"> </CreateNote>
</div>
 
</template>

<style scoped>
  .section-insert{
    width: 50%;
  }
  
</style>
