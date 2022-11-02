<script setup>

import { ref } from 'vue';

  const authorName = ref('Raeesa Parker');

  const newDate = new Date;

  const currentYear = newDate.getFullYear();

  const hrefAddress = ref("https://raeesaparker.github.io/portfolio/");


</script>

<template>
  <div>
    <footer class="footer mt-auto py-3 ">
      <div class="container">
        <a v-bind:href=hrefAddress target="__blank">&copy; {{authorName}} {{currentYear}}</a>
      </div>
    </footer>
  </div>
</template>

<style scoped>
  .footer {
    align-items: center;
    background-color: var(--yellow);
    bottom: 0;
    color:black;
    display: flex;
    font-size: 0.75rem;
    height: 5vh;
    justify-content: center;
    margin-left: -16px;
    position: absolute;
    width: 100vw;
  }

  .footer a {
    color: var(--black);
    margin: 0;
    text-decoration: none;
  }

  .footer a:hover{
    color: var(--blue);
  }

</style>
