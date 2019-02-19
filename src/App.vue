<template>
  <div id="app">
    <div>
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
    </div>

    <button @click="displayRandomRetro">Generate Random Retro</button>

    <h2>Suggested Retro</h2>

    <h3>Set the Stage</h3>
    <p>Title: </p>
    <p> {{ displayedWarmup.title }}</p>

    <h3>Gather data</h3>
    <p> {{ displayedFormat.title }}</p>   

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

      displayedWarmup: '',
      displayedFormat: '',

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
</style>
