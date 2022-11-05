<script setup>
  import { ref } from 'vue';

  const props = defineProps({
    placeholder : {
      type : String
    },
    value : {
      type: String
    },
    name : {
      type: String
    }
  })
  
</script>


<!-- =========================================================================================== -->
<!-- =========================================================================================== -->
<!-- =========================================================================================== -->

<template>
    <input required autocomplete="off" type="text" :placeholder=props.placeholder :value=props.value :name=props.name  />
</template>


<!-- =========================================================================================== -->
<!-- =========================================================================================== -->
<!-- =========================================================================================== -->


<style scoped>

input[type=text] {
  border-style: none;
  display: block;
  font-size: 1.0rem;
  margin-top: 5px;
  padding: 5px 0;
  width: 100%;
}

</style>
