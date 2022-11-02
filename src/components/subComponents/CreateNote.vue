<script setup>
  import { ref } from 'vue';

  const props = defineProps({
    title:{
      type: String, 
    },
    body:{
      type: String,
    }
  })




</script>

<template>
  <div class='note'>
      <h1> {{props.title}} </h1>
      <p> {{props.body}}  </p>
  </div>
 
</template>

<style scoped>
  .note {
  background-color: white;
  border-radius: 7px;
  box-shadow: 0 0 5px 0 rgba(0, 0, 0, 0.2);
  margin: 0.5rem;
  width: 200px;
  padding: 10px;
  float: left;
  }
  
</style>
