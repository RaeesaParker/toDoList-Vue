<script setup>
  import { ref, reactive} from 'vue';
  import InsertNote from './subComponents/InsertNote.vue';
  import ToDo from './ToDo.vue';
  import Doing from './Doing.vue';
  import Archive from './Archive.vue'

  // ============================================================= 
  // CREATE ARRAYS & FUNCTIONS
  // ============================================================= 

  // Create an array to store the current notes
  let noteList = ref([]);

  // Create an array to store the doing notes
   let doingNoteList = ref([]);

  // Create an array to store the archive/done notes
  let doneNoteList = ref([]);

  //  Function to add a new note => takes old noteList and adds new one to the end
  const addNoteFunc = (note) => {
    noteList.value = [...noteList.value, { noteId: noteList.value.length, noteTitle: note.noteTitle, noteContent: note.noteContent }]
  };

</script>

<!-- =========================================================================================== -->
<!-- =========================================================================================== -->
<!-- =========================================================================================== -->

<!-- Create input for note => Insert current todos => doing list => archive list -->

<template>

  <div class="section-insert">
    <InsertNote @onAdd=addNoteFunc > </InsertNote>
    <ToDo :noteList=noteList :doingNoteList=doingNoteList :doneNoteList=doneNoteList > </ToDo>
  </div>

  <div class='section-storage-container'>
    <Doing class="section-doing" :doingNoteList=doingNoteList :doneNoteList=doneNoteList :noteList=noteList > </Doing>
    <Archive class="section-archive" :doneNoteList=doneNoteList > </Archive>
  </div>

</template>


<!-- =========================================================================================== -->
<!-- =========================================================================================== -->
<!-- =========================================================================================== -->

<style scoped>
  .section-insert{
    min-width: 60%;
  }
  .section-storage-container{
    display: flex;
    flex-direction: column;
    min-height: 85vh;
    min-width: 40vw;
  }
  .section-archive{
    border-left: 1px solid var(--yellow);
    min-height: 45vh;
    
  }
  .section-doing{
    border-left: 1px solid var(--yellow);
    border-bottom: 1px solid var(--yellow);
    min-height: 42.5vh;
    margin: 0;
  }
  
</style>
