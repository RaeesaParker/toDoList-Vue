<script setup>
import { ref, reactive} from 'vue';
import CreateNote from './subComponents/CreateNote.vue';

  // Define props for Doing Note List
  const props = defineProps({
    doneNoteList: Object
  })


  // Function to delete note => Returns all the notes WITHOUT supplied ID
  const deleteNoteFunc = (id) => {
    props.doneNoteList.splice(id , 1)
  }

</script>


<template>
  <div>
    <h3>Done</h3>
    <CreateNote v-for="(note, index) in props.doneNoteList" :key="note.noteId" :noteItem="note" 
    @onDelete="deleteNoteFunc" 
    > </CreateNote>
  </div>
  
</template>




<style scoped>

</style>
