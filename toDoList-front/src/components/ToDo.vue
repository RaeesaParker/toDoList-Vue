<script setup>
  import CreateNote from './subComponents/CreateNote.vue';

  // Define props for todo, doing & done notelist
  const props = defineProps({
    noteList:Object,
    doingNoteList: Object,
    doneNoteList: Object
  })

  // Function to delete note => Removes the note with the supplied ID
  const deleteNoteFunc = (id) => {
    props.noteList.splice(id , 1)
  }


  // ---------------------------------------------------------------------------//
  // ----------------------- FUNCTIONS FOR DOING NOTE LIST -------------------- //
  // ---------------------------------------------------------------------------//

  //  Function to add a new note to the doing note list
  const addDoingNoteFunc = (note) => {
    
    let positionInsert = props.doingNoteList.length + 1 ;
    props.doingNoteList.splice( positionInsert , 0 , { noteId: note.noteId, noteTitle: note.noteTitle, noteContent: note.noteContent } )
    
    // Delete from the note from the main noteList 
    props.noteList.splice(note.noteId , 1)
  };

  // ---------------------------------------------------------------------------//
  // ----------------------- FUNCTIONS FOR DONE NOTE LIST -------------------- //
  // ---------------------------------------------------------------------------//
    
  //  Function to add a new note to the done note list
  const addDoneNoteFunc = (note) => {
    let positionInsert = props.doneNoteList.length + 1
    props.doneNoteList.splice( positionInsert , 0 , { noteId: note.noteId, noteTitle: note.noteTitle, noteContent: note.noteContent } )
    
    // Delete from the note from the main noteList 
    props.noteList.splice(note.noteId , 1)
  };

</script>

<!-- =========================================================================================== -->
<!-- =========================================================================================== -->
<!-- =========================================================================================== -->

<template>

  <CreateNote v-for="(note, index) in props.noteList" :key="note.noteId" :noteItem="note" 
    @onDelete="deleteNoteFunc" 
    @onDoingAdd="addDoingNoteFunc"
    @onDoneAdd="addDoneNoteFunc" 
    :doneToggle = false 
    :startToggle = false 
   >
     
  </CreateNote>

</template>

<!-- =========================================================================================== -->
<!-- =========================================================================================== -->
<!-- =========================================================================================== -->

<style scoped>

</style>
