<script setup>
import { stringifyQuery } from 'vue-router';


  // Create object to store user settings 
  const user = {
    userName: '',
    projectName:'',
    newUser: 'true',
  }

  // Emit onAdd function
  const emit = defineEmits(['onSetUser'])

  // Function to emit note when onSet has been pressed
  function onSet(){
    // Set new user to false
    user.newUser = 'false';
    emit('onSetUser', user)
  }
  
  // Function to set userName
  const  changeUserName = (userName, event) => {
    user.userName = event.target.value;
  }

  // Function to set project Name
  const  changeProjectName = (projectName, event) => {
    user.projectName = event.target.value;
  }

</script>




<template>

  <div class='section-homescreen'>
    <form @submit.prevent ='onSet'>
      <input autocomplete="off" type="text" placeholder="Name" name="name" :value=user.userName @change="changeUserName(user,$event)" /> 
      <input autocomplete="off" type="text" placeholder="Project Name" name="project-name" :value=user.projectName  @change="changeProjectName(user,$event)" /> 
      <button type="submit"> Submit </button>
    </form>
  </div>

</template>



<style scoped>

  .section-homescreen{
    display: flex;
    justify-content: center;
    align-items: center;
  }


</style>
