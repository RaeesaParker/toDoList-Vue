<script setup>
  import { ref, reactive} from 'vue';
  import InsertNote from './InsertNote.vue';
  import CreateNote from './CreateNote.vue';
  import Doing from '../Doing.vue';


  // Create an array to store the current notes
  let noteList = ref([]);

  // Create an array to store the doing notes
   let doingNoteList = ref([]);


  //  Function to add a new note => takes created note and pushes to the notelist
  const addDoingNoteFunc = (note) => {
    doingNoteList.value = [...doingNoteList.value, { noteId: doingNoteList.value.length, noteTitle: note.noteTitle, noteContent: note.noteContent }]
    
    // Delete from main noteList 
    noteList.value.splice(note.noteId , 1)
  };

  //  Function to add a new note => takes created note and pushes to the notelist
  const addNoteFunc = (note) => {
    noteList.value = [...noteList.value, { noteId: noteList.value.length, noteTitle: note.noteTitle, noteContent: note.noteContent }]
  };

  // Function to delete note => Returns all the notes WITHOUT supplied ID
  const deleteNoteFunc = (id) => {
    noteList.value.splice(id , 1)
  }


</script>

<template>
  <div class="section-insert">
  <InsertNote @onAdd=addNoteFunc > </InsertNote>
  <CreateNote v-for="(note, index) in noteList" :key="note.noteId" :noteItem="note" @onDelete="deleteNoteFunc" @onDoingAdd="addDoingNoteFunc"> </CreateNote>
  </div>
  <div class='section-storage-container'>
      <Doing :doingNoteList=doingNoteList > </Doing>
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
  
</style>
