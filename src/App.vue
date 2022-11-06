<script setup>
import { RouterLink, RouterView } from 'vue-router'
import { ref } from 'vue';
import Home from './components/Home.vue';
import Header from './components/Header.vue';
import mainSection from './components/mainSection.vue';
import Footer from './components/Footer.vue';

  // Define Username and Project
  let user = ref(['', '', '']);


  // Set the username and project
  function setUserFunc(name){
    user.value.splice(0 , 3 , name.userName, name.projectName, name.newUser)
  }

  // Reset the homescreen if newProject Button is clicked => sets user[2] to true
  function onNewProjectFunc(){
    user.value.splice(2 , 1 , "true")
  }

</script>

<template>
  <div id="app-body">
    <Home :class="{displayToggleNone: user[2] === 'false'}"   @onSetUser="setUserFunc"> </Home>
    <div  :class="{displayToggleBlock: user[2] === 'false'}"  class="displayToggleNone">
      <Header :userName=user[0] :projectName=user[1] :newUser=user[2] @onNewProject="onNewProjectFunc" ></Header>
      <mainSection></mainSection>
      <Footer></Footer>
    </div>

  </div>
</template>

<style scoped>

#app-body{
  position: relative;
}


.displayToggleNone{
  display: none;
}

.displayToggleBlock{
  display: block;
}

</style>
