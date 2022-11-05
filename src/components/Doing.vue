<script setup>
import { ref, reactive} from 'vue';
import CreateNote from './subComponents/CreateNote.vue';

  // Define props for Doing Note List
  const props = defineProps({
    doingNoteList: Object
  })


  // Function to delete note => Returns all the notes WITHOUT supplied ID
  const deleteNoteFunc = (id) => {
    props.doingNoteList.splice(id , 1)
  }

</script>


<template>
  <h3>Doing</h3>
  <CreateNote v-for="(note, index) in props.doingNoteList" :key="note.noteId" :noteItem="note" @onDelete="deleteNoteFunc" > </CreateNote>

</template>




<style scoped>

</style>
