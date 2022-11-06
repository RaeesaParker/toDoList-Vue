<script setup>
  // Define props for todo note list
  const props = defineProps({
    noteItem: Object,
    startToggle:Boolean,
    doneToggle:Boolean
  })


  // Function to emit functions for buttons pressed
  const emit = defineEmits([ 'onDoingAdd', 'onDoneAdd', 'onDelete'])

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
        class='button'
        id="doing-button"
        type="submit"> 
          <span class="hovertext" data-hover="Start Task"> <font-awesome-icon icon="fa-solid fa-play" />   </span>
      </button>

      <button  @click="onDoneAdd"
        :class="{displayToggle: props.doneToggle === true}"
        class='button'
        id="archive-button"
        title="Done"
        type="submit"> 
        <span class="hovertext" data-hover="Done"> <font-awesome-icon icon="fa-solid fa-circle-check" />   </span>
        </button>

      <button @click="onDelete"
        class='button'
        id="delete-button"
        title="Bin"
        type="submit"> 
        <span class="hovertext" data-hover="Trash"> <font-awesome-icon icon="fa-solid fa-trash" />   </span>
      </button>
    </div>

  </div>

</template>

<!-- =========================================================================================== -->
<!-- =========================================================================================== -->
<!-- =========================================================================================== -->

<style scoped>
  .note {
  background-color: var(--tertiary);
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

  #delete-button{
    color: var(--black);
  }

  #doing-button{
  color: var(--primary);
  }

  #archive-button{
    color: var(--red);
  }
  .displayToggle{
    display: none;
  }

  .hovertext {
  position: relative;
  }

.hovertext:before {
  background-color: var(--black);
  border-radius: 5px;
  color: var(--white);
  content: attr(data-hover);
  left: -300%;
  opacity: 0.5;
  padding: 5px 0;
  position: absolute;
  text-align: center;
  top: 200%;
  visibility: hidden;
  width: 75px;
  z-index: 1;
}

.hovertext:hover:before {
  opacity: 1;
  visibility: visible;
}


</style>
