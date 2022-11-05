<script setup>
  import { ref, reactive} from 'vue';
  import CreateNote from './subComponents/CreateNote.vue';


  // Define props for Doing Note List => array of all the notes in the doing note list
  const props = defineProps({
    noteList:Object,
    doingNoteList: Object,
    doneNoteList: Object
  })

  // ---------------------------------------------------------------------------//
  // ----------------------- FUNCTIONS FOR MAIN NOTE LIST --------------------- //
  // ---------------------------------------------------------------------------//
  
  // Function to delete note => Removes the note with the supplied ID
  const deleteNoteFunc = (id) => {
    props.noteList.splice(id , 1)
  }


  // ---------------------------------------------------------------------------//
  // ----------------------- FUNCTIONS FOR DOING NOTE LIST -------------------- //
  // ---------------------------------------------------------------------------//

  //  Function to add a new note to the doing note list
  const addDoingNoteFunc = (note) => {
    let positionInsert = props.doingNoteList.length + 1
    props.doingNoteList.splice( positionInsert , 0 , { noteId: props.doingNoteList.length, noteTitle: note.noteTitle, noteContent: note.noteContent } )
    
    // Delete from the note from the main noteList 
    props.noteList.splice(note.noteId , 1)
  };

  // ---------------------------------------------------------------------------//
  // ----------------------- FUNCTIONS FOR DONE NOTE LIST -------------------- //
  // ---------------------------------------------------------------------------//
    
  //  Function to add a new note to the done note list
  const addDoneNoteFunc = (note) => {
    let positionInsert = props.doneNoteList.length + 1
    props.doneNoteList.splice( positionInsert , 0 , { noteId: props.doneNoteList.length, noteTitle: note.noteTitle, noteContent: note.noteContent } )
    
    // Delete from the note from the main noteList 
    props.noteList.splice(note.noteId , 1)
    
  };


</script>

<template>
  <CreateNote v-for="(note, index) in props.noteList" :key="note.noteId" :noteItem="note" 
    @onDelete="deleteNoteFunc" 
    @onDoingAdd="addDoingNoteFunc"
    @onDoneAdd="addDoneNoteFunc"
    > </CreateNote>

  
</template>

<style scoped>
  .section-insert{
    width: 50%;
  }

  .section-storage-container{
  background-color: rebeccapurple;
  min-height: 85vh;
  min-width: 50vw;
}

.section-archive{
  background-color: yellow;
  border-left: 1px solid var(--black);
  min-height: 42.5vh;
}

.section-doing{
  border-left: 1px solid var(--black);
  border-bottom: 1px solid var(--black);
  min-height: 42.5vh;
  margin: 0;
}
  
</style>
