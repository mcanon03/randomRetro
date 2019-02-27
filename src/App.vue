<template>
  <div id="app">
    <!-- <div>
      <h1>Select info about your team and prep time</h1>
    </div>
    
    <div>
      <div>
      Team Makeup
        <select v-model="formData.teamMakeUp">
          <option v-for="(teamMakeUp, index) in teamMakeUps" :key="index">
            {{ teamMakeUp }}
          </option>
        </select>
    </div>

      <div>
      Team Size
        <select v-model="formData.teamSize">
          <option v-for="(teamSize, index) in teamSizes" :key="index">
            {{ teamSize }}
          </option>
        </select>
      </div>

      <div>
      Prep Time
        <select v-model="formData.prepTime">
          <option v-for="(prepTime, index) in prepTimes" :key="index">
            {{ prepTime }}
          </option>
        </select>
      </div>
    </div> -->

    <button @click="displayRandomRetro">Generate Random Retro</button>

    <h2>Suggested Retro</h2>

    <h3>Set the Stage</h3>
    
    <div class="row-group">
      <p>Title: </p>
      <p> {{ displayedWarmup.title }}</p>
    </div>

    <div class="row-group">
      <p>Delivery: </p>
      <p> {{ displayedWarmup.delivery }}</p>
    </div>

    <div class="row-group">
      <p>Goal: </p>
      <p> {{ displayedWarmup.goal }}</p>
    </div>


    <h3>Gather data</h3>

    <div class="row-group">
      <p>Title: </p>
      <p> {{ displayedFormat.title }}</p>  
    </div>
 
     <div class="row-group">
      <p>Delivery: </p>
      <p> {{ displayedFormat.delivery }}</p>  
    </div>

  </div>
</template>

<script>
import { warmups } from './retroInfo/warmups.json'
import { retroFormats } from './retroInfo/retroFormats.json'
import { teamMakeUps, teamSizes, prepTimes } from './retroInfo/teamInfo.json'

export default {
  name: 'app',
  components: {
  },
  data() {
    return {
      warmups,
      retroFormats,
      teamMakeUps, 
      teamSizes, 
      prepTimes,

      formData: {
        teamMakeUp: '',
        teamSize: '',
        prepTime: ''
      },

      displayedWarmup: warmups[0],
      displayedFormat: retroFormats[0],

      filteredWarmups: '',
      filteredFormats: ''
    }
  },
  methods: {
    displayRandomRetro() {
      // console.log(this.warmups);

      // console.log(this.filteredWarmups);
      this.displayedWarmup = this.warmups[Math.floor(Math.random()*this.warmups.length)];
      this.displayedFormat = this.retroFormats[Math.floor(Math.random()*this.retroFormats.length)];
    }
  }
}
</script>

<style>
#app {
  font-family: 'Aaux Next'
}

.row-group p {
    display: inline-block
}

p:first-of-type {
  margin-right: 1rem;
}
</style>
