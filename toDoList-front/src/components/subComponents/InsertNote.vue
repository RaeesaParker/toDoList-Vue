<script setup>
  import InsertNoteInput from './InsertNoteInput.vue';

  // Emit onAdd function
  const emit = defineEmits(['onAdd'])

  // Function to emit note when onAdd has been pressed
  function onAdd(){
    emit('onAdd', note)

    // Clear the form fields => reset the note content
    const form = document.getElementById('input-form')

    form.reset()
    note.noteId = 0 ;
    note.noteTitle = '' ; 
    note.noteContent = '';

  }
  
  // Create object to store the note
  const note = {
    noteId: Math.random() , 
    noteTitle: '', 
    noteContent: ''
  }

  // Function to set note title
  const  changeNoteTitle = (note, event) => {
    note.noteTitle = event.target.value;
  }

  // Function to set note content
  const  changeNoteContent = (note, event) => {
    note.noteContent = event.target.value;
  }

</script>

<!-- =========================================================================================== -->
<!-- =========================================================================================== -->
<!-- =========================================================================================== -->

<template>

  <h2>To Do</h2>

  <div class="insert-note"> 

    <form id="input-form" @submit.prevent ='onAdd'>

      <InsertNoteInput
        type='text'
        id="noteTitleID"
        name='noteTitle'
        placeholder='Task Name'
        :value = note.noteTitle
        @change="changeNoteTitle(note,$event)"
      />

      <InsertNoteInput
        type='text'
        id="noteContentID"
        name='noteContent'
        placeholder='Task Details'
        :value = note.noteContent
        @change="changeNoteContent(note,$event)"
      />

      <button
      class='submit-note-button'
      type='submit'
      >
      +
      </button>

    </form>
  </div>
 
</template>

<!-- =========================================================================================== -->
<!-- =========================================================================================== -->
<!-- =========================================================================================== -->

<style scoped>
.insert-note {
background-color: var(--tertiary);
border-radius: 7px;
box-shadow: 0 0 5px 0 rgba(0, 0, 0, 0.2);
height: 100px;
margin: 15px auto 15px auto;
padding: 10px;
width: 60%;
}

.submit-note-button{
  align-items: center;
  background-color: var(--primary);
  border-radius: 50%;
  border-style: none;
  color: var(--secondary);
  display: flex;
  font-size: 1.0rem;
  font-weight: 600;
  justify-content: center;
  padding: 0 1px 2px 2px ;
  position: relative;
  right:-90%;
  width: 2.0rem;
 }
</style>
