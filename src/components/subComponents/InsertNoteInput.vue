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

  console.log(props.value)

</script>

<template>
  <div>
    <input autocomplete="off" type="text" :placeholder=props.placeholder :value=props.value :name=props.name  />
  </div>
 
</template>

<style scoped>

input[type=text] {
  display: block;
  margin-top: 7px;
  border-style: none;
  font-size: 0.75rem;
  width: 100%;
}

</style>
