<template>
  <div id=app>
    <div class="flexwrap">
      <div class="empty-space"></div>
      <div class="main-content">
        <Stages v-bind:stages="stages" v-on:change-index="changeIndex" />
        <ListOfSteps v-bind:steps="steps" v-on:toggle-description="toggleDescription"/>
      </div>
      <div class="empty-space"></div>
    </div>
  </div>
</template>

<script>
//import HelloWorld from './components/HelloWorld.vue'
import Stages from './components/Stages.vue'
import ListOfSteps from './components/ListOfSteps.vue'

export default {
  name: 'App',
  components: {
    Stages,
    ListOfSteps,
    //StepItem
  },
  data(){
    let cross = {
      index: 0,
      name: 'Cross',
      steps: [
        {
          name: 'Daisy',
          description: 'Can be skipped. <a target="_blank" rel="noopener noreferrer" href="http://www.google.com/">This is a link</a>',
          hiddenDescription: true
        },
        {
          name: 'Regular cross',
          description: 'JUST DO IT!',
          hiddenDescription: true
        },
        {
          name: '8 moves or less',
          description: 'Look for how the moves to solve the easy pieces can be used to help solving the harder ones.',
          hiddenDescription: true
        },
        {
          name: 'Blindfold practice',
          description: 'Give yourself unlimited inspection. Try to plan the entire cross and then solve it blindfolded.',
          hiddenDescription: true
        },
        {
          name: 'Cross + corner',
          description: 'Find an F2L corner that will end up in the top layer after the cross is done. This will help with the transition from cross to F2L.',
          hiddenDescription: true
        },
        {
          name: 'Cross + 1',
          description: 'Plan out both cross and the first pair during inspection.',
          hiddenDescription: true
        },
        {
          name: 'X-cross',
          description: 'Solve cross and first pair simultaniously.',
          hiddenDescription: true
        }
      ]
    }

    let f2l = {
      index: 1,
      name:'F2L',
      steps: [
          {
            name: 'Basic',
            description: 'Do it.',
            hiddenDescription: true
          },
          {
            name: 'Improve',
            description: 'Do it better.',
            hiddenDescription: true
          }
      ]
    }

    let oll = {
      index: 2,
      name: 'OLL',
      steps: [
        {
          name: 'Beginner variant',
          description: 'Orient edges with F sexy F\', corners with Sune.',
          hiddenDescription: true
        },
        {
          name: '2 Look OLL',
          description: 'Edges with one of 4 algs, corners with one of 7.',
          hiddenDescription: true
        }
      ]
    }

    let pll = {
      index: 3,
      name: 'PLL',
      steps: [
        {
          name: 'Beginner variant',
          description: 'Do it easy.',
          hiddenDescription: true
        },
        {
          name: '2 Look PLL',
          description: `
          <p>Do the ting.</p>
          <p>Do the other thing.</p>
          `,
          hiddenDescription: true
        },
        {
          name: 'Full PLL',
          description: 'It\'s easy.',
          hiddenDescription: true
        }
      ]
    }
    let stages = [cross, f2l, oll, pll];
    
    return{
      stages: stages,
      steps: stages[0].steps
    }
  },
  methods: {
    changeIndex(index, element){
      this.steps = this.stages[index].steps;

      let stages = document.getElementsByClassName("stage");
      stages.forEach(stage => stage.classList.add("stage-background-color"));
      element.classList.remove("stage-background-color");
      element.classList.add("selected-stage-background-color");
    },
    toggleDescription(name){
      
      let step = this.steps.filter(step => step.name == name)[0];
      if(step.hiddenDescription == false){
        step.hiddenDescription = true;
        return;
      }

      this.steps.forEach(step => step.hiddenDescription = step.name != name ? true : false)
      
      step.hiddenDescription = false //!step.hiddenDescription;
    }
  },
  mounted(){
    let firstStage = document.getElementsByClassName("stage")[0];
    firstStage.classList.remove("stage-background-color");
    firstStage.classList.add("selected-stage-background-color");
  }

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  /* color: #2c3e50; */
  margin-top: 10px;
  width: 100%;
}

.flexwrap{
  display: flex;

}

.empty-space{
  flex-grow: 1;
}
.main-content{
  max-width: 600px;
  min-width: 400px;
  flex-grow: 100000;
}
.selected-stage-background-color{
  background-color: #9ea7d8;
}
</style>
