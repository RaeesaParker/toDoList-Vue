<script setup>
  import { ref, reactive} from 'vue';
  import InsertNote from './InsertNote.vue';
  import CreateNote from './CreateNote.vue';
  import Doing from '../Doing.vue';
  import Archive from '../Archive.vue'

  // ---------------------------------------------------------------------------//
  // -------- CREATE ARRAYS TO STORE NOTES, DOING NOTES, & DONE NOTES --------- //
  // ---------------------------------------------------------------------------//
  
  // Create an array to store the current notes
  let noteList = ref([]);

  // Create an array to store the doing notes
   let doingNoteList = ref([]);

  // Create an array to store the archive/done notes
  let doneNoteList = ref([]);


  // ---------------------------------------------------------------------------//
  // ----------------------- FUNCTIONS FOR MAIN NOTE LIST --------------------- //
  // ---------------------------------------------------------------------------//

  //  Function to add a new note => takes old noteList and adds mew one to the end
  const addNoteFunc = (note) => {
    noteList.value = [...noteList.value, { noteId: noteList.value.length, noteTitle: note.noteTitle, noteContent: note.noteContent }]
  };

  // Function to delete note => Removes the note with the supplied ID
  const deleteNoteFunc = (id) => {
    noteList.value.splice(id , 1)
  }


  // ---------------------------------------------------------------------------//
  // ----------------------- FUNCTIONS FOR DOING NOTE LIST -------------------- //
  // ---------------------------------------------------------------------------//

  //  Function to add a new note to the doing note list
  const addDoingNoteFunc = (note) => {
    doingNoteList.value = [...doingNoteList.value, { noteId: doingNoteList.value.length, noteTitle: note.noteTitle, noteContent: note.noteContent }]
    
    // Delete from the note from the main noteList 
    noteList.value.splice(note.noteId , 1)
  };

  // ---------------------------------------------------------------------------//
  // ----------------------- FUNCTIONS FOR DONE NOTE LIST -------------------- //
  // ---------------------------------------------------------------------------//

  //  Function to add a new note to the done note list
  const addDoneNoteFunc = (note) => {
    console.log("The done add func list has the form", doneNoteList.value)
    doneNoteList.value = [...doneNoteList.value, { noteId: doneNoteList.value.length, noteTitle: note.noteTitle, noteContent: note.noteContent }]
    
    // Delete from the note from the main noteList 
    noteList.value.splice(note.noteId , 1)
    
  };


</script>

<template>
  <div class="section-insert">
  <InsertNote @onAdd=addNoteFunc > </InsertNote>
  <CreateNote v-for="(note, index) in noteList" :key="note.noteId" :noteItem="note" 
    @onDelete="deleteNoteFunc" 
    @onDoingAdd="addDoingNoteFunc"
    @onDoneAdd="addDoneNoteFunc"
    > </CreateNote>
  </div>
  <div class='section-storage-container'>
      <Doing class="section-doing" :doingNoteList=doingNoteList :doneNoteList=doneNoteList :noteList=noteList> </Doing>
      <Archive class="section-archive" :doneNoteList=doneNoteList > </Archive>
  </div>
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
