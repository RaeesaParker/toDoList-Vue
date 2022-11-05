<script setup>
  // Define props for todo note list
  const props = defineProps({
    noteItem: Object
  })

  // Function to emit functions for buttons pressed
  const emit = defineEmits([ 'onDoingAdd', 'onDoneAdd', 'onDelete',])

  function onDoingAdd() { emit('onDoingAdd', props.noteItem) }

  function onDoneAdd(){ emit('onDoneAdd', props.noteItem) }

  function onDelete(){ emit('onDelete', props.noteItem.noteId) }

</script>

<!-- =========================================================================================== -->
<!-- =========================================================================================== -->
<!-- =========================================================================================== -->

<template>

  <div class='note'>
    <h1> {{props.noteItem.noteTitle}} </h1>
    <p> {{props.noteItem.noteContent}}  </p>

    <div class='div-buttons'>
      <button @click="onDoingAdd"
        class='button doing-button'
        type="submit"
        > Start
      </button>

      <button  @click="onDoneAdd"
          class='button archive-button'
          type="submit"
          > Done
        </button>

      <button @click="onDelete"
        class='button delete-button'
        type="submit"
        > Delete
      </button>
    </div>

  </div>

</template>

<!-- =========================================================================================== -->
<!-- =========================================================================================== -->
<!-- =========================================================================================== -->

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

  .div-buttons{
  display: flex;
  justify-content: space-between;
  }

  .button{
    background-color: transparent;
    border: none;
    cursor: pointer;
    font-size: 0.75rem;
    font-weight: 600;
    margin-top: 20px;
    outline: none;
  }

  .delete-button{
    color: var(--yellow);
    display: inline;
  }
  .doing-button{
  color: var(--red);
  display: inline;
  }

  .archive-button{
    color: var(--black);
    display: inline;
  }

  
</style>
