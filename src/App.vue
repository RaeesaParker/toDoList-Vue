<script setup>
import { RouterLink, RouterView } from 'vue-router'
import Header from './components/Header.vue';
import mainSection from './components/mainSection.vue';
import Footer from './components/Footer.vue';

</script>

<template>
  <div id="app-body">
    <Header></Header>
    <mainSection></mainSection>
    <Footer></Footer>
  </div>
</template>

<style scoped>

#app-body{
  position: relative;
}

</style>
