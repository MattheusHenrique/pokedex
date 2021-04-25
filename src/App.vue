<template>
  <div id="app">
    <h2>{{ title }}</h2>
      <label for='name'>
        <input v-on:keyup.enter="getPokemon" class='form-control' name='name' id="search" type="text" placeholder='Name:' required>
      </label>
      <Pokemon  v-for="pokemon in pokemonsFilter" :key="pokemon" :pokemon="pokemon"/>
  </div>
</template>

<script>
import Pokemon from './components/Pokemon.vue'
import axios from 'axios'

export default {

  data(){
    return{
      title: "Pokedex",
      pokemondex:{
        url:'https://pokeapi.co/api/v2/pokemon',
        },
      pokemons:[],
      pokemonsFilter:[],
    }
  }, 

  components: {
    Pokemon,
  },

  methods:{
    getPokemon(e){
    
      const {url} = this.pokemondex;
      for(let i = 0; i < 20; i++){
        axios.get(`${url}/${i}`)
           .then(({data}) => (this.pokemons.push(data)));
      }

      const name_pokemon = e.target.value;
      if(name_pokemon == '' ||  name_pokemon == ' '){
        this.pokemonsFilter = this.pokemons;
        console.log(this.pokemonsFilter); 
      }else{
         this.pokemonsFilter = this.pokemons.filter(result => result.name.indexOf(name_pokemon) != -1);
      }
    }
  },

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

body{ 
  background: #348F50;  /* fallback for old browsers */
  background: -webkit-linear-gradient(to right, #56B4D3, #348F50);  /* Chrome 10-25, Safari 5.1-6 */
  background: linear-gradient(to right, #56B4D3, #348F50); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */
}

label{
    font-size: 20px;
    font-style: italic
}


input{
  width: 20%;
  padding: 10px 20px;
  margin: 10px 0;
  border: 1px solid #ccc;
  border-radius: 20px;
  box-sizing: border-box;
}

input, select{
    box-shadow: 0 0 0 0;
    outline: 0;
}

.find{
  display: inline-block;
}
</style>
