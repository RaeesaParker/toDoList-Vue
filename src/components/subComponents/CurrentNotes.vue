<script setup>
  import { ref, reactive} from 'vue';
  import InsertNote from './InsertNote.vue';
  import CreateNote from './CreateNote.vue';


  // Create an array to store the notes
  let noteList = ref([  
]);

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

  <CreateNote v-for="(note, index) in noteList" :key="note.noteId" :noteItem="note" @onDelete="deleteNoteFunc" > </CreateNote>
</div>
 
</template>

<style scoped>
  .section-insert{
    width: 50%;
  }
  
</style>
