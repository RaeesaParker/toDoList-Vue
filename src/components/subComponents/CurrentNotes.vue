<script setup>
  import { ref } from 'vue';
  import InsertNote from './InsertNote.vue';
  import CreateNote from './CreateNote.vue';



</script>

<template>
  <div class="section-insert">

    <InsertNote> </InsertNote>
  <CreateNote title="Hello" body="something"> </CreateNote>
</div>
 
</template>

<style scoped>
  .section-insert{
    width: 50%;
  }
  
</style>
