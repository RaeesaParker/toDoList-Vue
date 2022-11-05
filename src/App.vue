<script setup>
import { RouterLink, RouterView } from 'vue-router'
import { ref } from 'vue';
import Home from './components/Home.vue';
import Header from './components/Header.vue';
import mainSection from './components/mainSection.vue';
import Footer from './components/Footer.vue';

  // Define Username and Project
  let user = ref([]);

  // Set the username and project
  function setUserFunc(name){
    user.value.splice(0 , 0 , name.userName, name.projectName)
  }

</script>

<template>
  <div id="app-body">
    <Home id="section-home"  @onSetUser="setUserFunc"> </Home>
    <Header  :userName=user[0] :projectName=user[1] ></Header>
    <mainSection></mainSection>
    <Footer></Footer>
  </div>
</template>

<style scoped>

#app-body{
  position: relative;
}

#section-home{
  background-color: bisque;
  height: 100vh;
}

</style>
