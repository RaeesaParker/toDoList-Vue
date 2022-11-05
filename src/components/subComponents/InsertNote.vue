<script setup>
  import { ref } from 'vue';
  import InsertNoteInput from './InsertNoteInput.vue';
  
  const emit = defineEmits(['onAdd'])


  function onAdd(){
    emit('onAdd', note)
  }
  

 const note = {
    noteId: 0 , 
    noteTitle: '', 
    noteContent: ''
  }

    // Create function to add a new note to the array => Takes the input title / content and sets them
    const  changeNoteTitle = (note, event) => {
      note.noteTitle = event.target.value;
    }

      // Create function to add a new note to the array => Takes the input title / content and sets them
      const  changeNoteContent = (note, event) => {
        note.noteContent = event.target.value;
    }





</script>

<template>
  <h3>Create Task</h3>
  <div class="insert-note"> 
<form @submit.prevent ='onAdd'>
  <InsertNoteInput
    type='text'
    name='noteTitle'
    placeholder='Task Name'
    :value = note.noteTitle
    @change="changeNoteTitle(note,$event)"
  />
  <InsertNoteInput
    type='text'
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

<style scoped>
.insert-note {
background-color: white;
border-radius: 7px;
box-shadow: 0 0 5px 0 rgba(0, 0, 0, 0.2);
height: 75px;
margin: 15px auto 15px auto;
padding: 10px;
width: 60%;
}

.submit-note-button{
  align-items: center;
  background-color: var(--yellow);
  border-radius: 50%;
  border-style: none;
  color: var(--black);
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
