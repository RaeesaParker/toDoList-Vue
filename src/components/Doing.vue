<script setup>
import CreateNote from './subComponents/CreateNote.vue';

  // Define props for todo, doing, and done note lists
  const props = defineProps({
    noteList:Object,
    doingNoteList: Object,
    doneNoteList: Object,
  })

  // Function to delete note from the doing list => removes note with supplied id
  const deleteNoteFunc = (id) => {
    props.doingNoteList.splice(id , 1)
  }

  // Function to add note to the done list 
  const addDoneNoteFunc = (note) => {
    let positionInsert = props.doneNoteList.length + 1
    props.doneNoteList.splice( positionInsert , 0 , { noteId: props.doneNoteList.length, noteTitle: note.noteTitle, noteContent: note.noteContent } )

    // Delete from the note from the doing noteList 
    props.doingNoteList.splice(note.noteId , 1)
  }

</script>

<!-- =========================================================================================== -->
<!-- =========================================================================================== -->
<!-- =========================================================================================== -->

<template>

  <div>
    <h2>Doing</h2>
    <CreateNote v-for="(note, index) in props.doingNoteList" :key="note.noteId" :noteItem="note"
      :doneToggle = false
      :startToggle = true
      @onDelete="deleteNoteFunc"
      @onDoneAdd="addDoneNoteFunc"> 
    </CreateNote>
  </div>

</template>


<!-- =========================================================================================== -->
<!-- =========================================================================================== -->
<!-- =========================================================================================== -->

<style scoped>

</style>
