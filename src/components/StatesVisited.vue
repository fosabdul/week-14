<template>

<div> 
  <h2> States you have visited</h2>

  <p v-for="state in statesvisited" v-bind:key="state.name">
      {{ state.name}}
  </p>
  
</div>
</template>

<script>



export default {

  name: 'statesvisited', 
  data() {
      return {
          statesvisited: [] 
      }
  },
  mounted() {
          this.$stateService.getVisited().then(StatesVisited => {
              this.statesvisited = StatesVisited
          }).catch(err => {
              alert('sorry unable to fetch lis of states you visited')
              console.error('error getting all the states',err)
          }) // this where you get all the states
      
      
  }
}
</script>

<style scoped>

.state-list-container {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-evenly;
}

.state-container {
    margin: 1rem;
}
</style>
