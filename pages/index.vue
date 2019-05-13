<template>
  <section class="hero is-medium is-primary is-bold">
    <section class="container">
      <div class="hero-body">
        <div class="container">
          <h1 class="title is-1 is-center">
            Rick and Morty characters
          </h1>
          <h2 class="subtitle is-3">
            all the characters of the serie
          </h2>
        </div>
      </div>
      <div class="columns is-multiline">
        <CharacterCard :character="character" v-for="character in characters" :key="character.id" />
      </div>
    </section>
  </section>
</template>

<script>
//Import Libraries
import axios from 'axios';

//import base endpoint
import env from '../config/env';

//Import Components
import CharacterCard from '../components/CharacterCard';

export default {
  name: 'IndexPage',
  components:{
    CharacterCard
  },
  data(){
    return{
      characters:[]
    }
  },
  created(){
    axios.get(`${env.endpoint}/character/`)
    .then(response =>{
      this.characters = response.data.results;
      console.log(response.data.info)
    })
  }
}
</script>

<style scoped>
.box{
  padding: 1em;
}
section.container{
  padding:  2em;
}
.hero-body{
  text-align: center;
}
</style>
