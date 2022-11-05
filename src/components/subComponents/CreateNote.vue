<script setup>
  // Define props for todo note list
  const props = defineProps({
    noteItem: Object,
    startToggle:Boolean,
    doneToggle:Boolean
  })

  console.log(props.startToggle)

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
    <div id="note-content">
      <h3> {{props.noteItem.noteTitle}} </h3>
      <p> {{props.noteItem.noteContent}}  </p>
    </div>


    <div class='div-buttons'>
      <button @click="onDoingAdd"
        :class="{displayToggle: props.startToggle === true}"
        class=' button doing-button'
        type="submit"
        > Start
      </button>

      <button  @click="onDoneAdd"
        :class="{displayToggle: props.doneToggle === true}"
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

  #note-content {
    word-break: break-all;
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
  }
  .doing-button{
  color: var(--red);
  }

  .archive-button{
    color: var(--black);
  }
  .displayToggle{
    display: none;
  }

  
</style>
