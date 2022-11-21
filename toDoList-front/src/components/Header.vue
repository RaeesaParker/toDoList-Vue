<script setup>

  const props = defineProps({
    userName: String,
    projectName: String,
    newUser:String
  })

  const emit = defineEmits([ 'onNewProject'])

  // When new projet is clicked => set newUser back to true 
  function onNewProject(){
    emit('onNewProject')
  }

  
</script>


<!-- =========================================================================================== -->
<!-- =========================================================================================== -->
<!-- =========================================================================================== -->


<template>
  <div>
      <nav class="navbar navbar-expand-lg  navbar-customise">
        <div class="container-fluid">
          <a class="navbar-brand" >{{props.userName}}'s Workspace</a>
          <a class="navbar-brand" id="project-name">{{props.projectName}}</a>
          <a class="navbar-brand" id="new-project" @click="onNewProject">New Project</a>
        </div>
      </nav>
    </div>
</template>


<!-- =========================================================================================== -->
<!-- =========================================================================================== -->
<!-- =========================================================================================== -->


<style scoped>
  .navbar-customise{
  background-color: var(--primary);
  border-radius: 1px;
  box-shadow: 0 0 10px 0 rgba(0, 0, 0, 0.3);
  height: 10vh;
  margin: auto -16px;
}

.navbar-brand{
  color: var(--black);
  cursor: default;
  font-family: var(--fontSerif);
  font-size: 2.0rem;
}

#project-name{
  color: var(--secondary);
}

#new-project{
  font-size: 1.25rem;
}

#new-project:hover{
  color: var(--secondary);
  cursor: pointer;
}

@media screen and (max-width: 1000px){
  .navbar-brand{
  font-size: 1.5rem;
}
}

</style>
