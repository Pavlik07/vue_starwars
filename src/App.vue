<template>
  <div id="app">
    <h1>Star Wars Characters</h1>
      <div class="cards">
        <HumanCard 
          v-for='human in people.results' 
          :key='human.name'
          :human='human'
        />
      </div>
  </div>
</template>

<script>
import HumanCard from './components/HumanCard'
export default {
  name: 'App',
  components: {
    HumanCard,
  },
  data() {
    return {
      people: {},
    }
  },
  mounted() {
    fetch('https://swapi.dev/api/people')
      .then(res => res.json())
      .then(data => this.people = data)
      .catch(err => console.log(err.message));
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.cards {
  display: flex;
  flex-wrap: wrap;
}
.cards>* {
  flex: 400px;
  width: fit-content
}
</style>
