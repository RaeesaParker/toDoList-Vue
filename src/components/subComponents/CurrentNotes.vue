<script setup>
  import { ref, reactive} from 'vue';
  import InsertNote from './InsertNote.vue';
  import CreateNote from './CreateNote.vue';


  // Create an array to store the notes
  let noteList = ref([  
  ]);

  //  Function to add a new note => takes created note and pushes to the notelist
  const addNoteFunc = (note) => {
    noteList.value = [...noteList.value, { noteTitle: note.noteTitle, noteContent: note.noteContent }]
    console.log(note.note)
    console.log(noteList.value)
  };



</script>

<template>
  <div class="section-insert">

  <InsertNote @onAdd=addNoteFunc > </InsertNote>

  <CreateNote v-for="(item, index) in noteList" :key="index" :noteItem="item" > </CreateNote>
</div>
 
</template>

<style scoped>
  .section-insert{
    width: 50%;
  }
  
</style>
