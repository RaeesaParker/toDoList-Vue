<script setup>
import { stringifyQuery } from 'vue-router';

  // Create object to store user settings 
  const user = {
    userName: '',
    projectName:'',
    newUser: 'true',
  }

  // Emit onAdd function
  const emit = defineEmits(['onSetUser'])

  // Function to emit note when form has been submitted
  function onSet(){
    // Set new user to false
    user.newUser = 'false';
    emit('onSetUser', user)

    // Check what colour has been submitted 
    const colourChosen =  document.querySelector('input[name="colour_chosen"]:checked').value;

    // Set the colour palette depending on which palette was chosen 
    switch (colourChosen){
      case 'green':
        document.documentElement.style.setProperty('--primary', '#4e705d');
        document.documentElement.style.setProperty('--secondary', '#e9e9e9');
        document.documentElement.style.setProperty('--tertiary', '#fcfcfc');
        break;
      case 'red':
        document.documentElement.style.setProperty('--primary', '#b01307');
        document.documentElement.style.setProperty('--secondary', '#f3f1ef');
        document.documentElement.style.setProperty('--tertiary', '#fffbfb');
        break;
      case 'blue':
        document.documentElement.style.setProperty('--primary', '#71a5de');
        document.documentElement.style.setProperty('--secondary', '#e1ecf7');
        document.documentElement.style.setProperty('--tertiary', '#f8f9fb');
        break;
      case 'yellow':
        document.documentElement.style.setProperty('--primary', '#eec302');
        document.documentElement.style.setProperty('--secondary', '#f4f4f4');
        document.documentElement.style.setProperty('--tertiary', '#ffffff');
        break;
      default:
        document.documentElement.style.setProperty('--primary', '#eec302');
        document.documentElement.style.setProperty('--secondary', '#f4f4f4');
        document.documentElement.style.setProperty('--tertiary', '#ffffff');
        break;
    }
  }
  
  // Function to set userName
  const  changeUserName = (userName, event) => {
    user.userName = event.target.value;
  }

  // Function to set project Name
  const  changeProjectName = (projectName, event) => {
    user.projectName = event.target.value;
  }

</script>




<template>

  <div class='section-homescreen'>
    <div class="home-subsection">
      <h1>Welcome to your Workspace!</h1>
      <h3>This is a flexible work management tool where you can ideate plans and your track progress in a visual, productive, and rewarding way. </h3>
      <h3>Fill in the form below to begin your project:</h3>
    </div>
    
    <div class="home-subsection">
      <div id="user-form">
        <form  @submit.prevent ='onSet'>
          <fieldset class="field-flex"> 
            <input required autocomplete="off" type="text" placeholder="Name" name="name" :value=user.userName @change="changeUserName(user,$event)" /> 
          </fieldset>

          <fieldset class="field-flex">
            <input required autocomplete="off" type="text" placeholder="Project Name" name="project-name" :value=user.projectName  @change="changeProjectName(user,$event)" /> 
          </fieldset>

          <fieldset  class="field-flex">
            <div class="colour-card">
              <label for="green">
                <div id="palette-green" class="colour-card-div"></div>
              </label><br/>
              <input checked type="radio" id="green" name="colour_chosen" value="green"><br/>
            </div>
            
            <div class="colour-card">
              <label for="red">
                <div id="palette-red" class="colour-card-div"></div>
              </label><br/>
              <input type="radio" id="red" name="colour_chosen" value="red"><br/>
            </div>
          
            <div class="colour-card">
              <label for="blue">
                <div id="palette-blue" class="colour-card-div"></div>
              </label><br/>
              <input type="radio" id="blue" name="colour_chosen" value="blue"><br/>
            </div>

            <div class="colour-card">
              <label for="yellow">
                <div id="palette-yellow" class="colour-card-div"></div>
              </label><br/>
              <input type="radio" id="yellow" name="colour_chosen" value="yellow"><br/>
            </div>
          </fieldset>      
          
          <button type="submit"> Submit </button>
        </form>
      </div>
    </div>
  </div>

</template>



<style scoped>

  .section-homescreen{
    align-items: center;
    display: flex;
    flex-direction: column;
    height: 100vh;
    justify-content: center;
  }

  h3{
    font-size: 1.1rem;
    font-weight: 500;
    line-height: 2rem;
    word-spacing: 0.25rem;
  }
  .home-subsection{
    width: 75vw;
    display: flex;
    flex-direction: column;
    justify-content: center;
  }

  #user-form{
    display: flex;
    justify-content: center;
    margin: 4% 0 0 0 ;
    width:100%;
  }
  .field-flex{
    display: flex;
    justify-content: center;
  }

  form{
    width: 100%;
  }

  input[type=text]{
    background: transparent;
    border: none;
    border-bottom: 1px solid var(--black);
    margin: 0 0 2% 0;
    padding: 1%;
    width: 50%
  }
  .colour-card{
    display: flex;
    flex-direction: column;
    padding: 5% 5% 2% 5%;
  }

  .colour-card-div{
    display: inline-block;
    border: 1px solid var(--black);
    border-radius: 15px;
    margin-bottom: 10%;
    min-width: 10vw;
	  min-height: 5vh;
  }

  #palette-green{
    background: linear-gradient(to right, #fcfcfc 33%, #e9e9e9 33%, #e9e9e9 66%, #4e705d 66% );
  }
  #palette-red{
    background: linear-gradient(to right, #fffbfb 33%, #f3f1ef 33%, #f3f1ef 66%, #b01307 66% );
  }
  #palette-blue{
    background: linear-gradient(to right, #f8f9fb 33%, #e1ecf7 33%, #e1ecf7 66%, #71a5de 66% );
  }
  #palette-yellow{
    background: linear-gradient(to right, #ffffff 33%, #f4f4f4 33%, #f4f4f4 66%, #eec302 66% );
  }
  
  #user-form button{
    background: transparent;
    border: none;
    display: flex;
    margin: 2% auto 0 auto;
  }

  #user-form button:hover{
    color: var(--blue);
    cursor: pointer;
  }
</style>
