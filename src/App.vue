<template>
  <header class="header">
    <label for="">
      escreva o nome do pokémon ou seu id
      <input 
        type="text" 
        v-model="pokemonID">
      <button 
        class="searchButton"
        @click="searchPokemon">Busca tu pokemon</button>
    </label>
  </header>
  
  <main 
    class="main"
    
    >
    <section class="pokemonCard">
      <div class="nameImage">
        <h1 class="pokemonName">{{pokemonData.name}}</h1>
        <img 
        :src="pokemonData.sprites" 
        :alt="pokemonData.name"
        >

      </div>
      <ul class="type">
      <h2>Type</h2>
        <li
          v-for="(type, index) in pokemonData.types"
          :key="index"
          :class="type.type.name"
        >
          <span>{{type.type.name}}</span>
        </li>
      </ul>
      <ul class="stats">
        <h2>stats</h2>
        <li
          v-for="(stat, index) in pokemonData.stats"
          :key="index"
        >
          <span>{{stat.stat.name}} => {{stat.base_stat}}</span>
        </li>
      </ul>
    </section>
  </main>
  
</template>


<script>
  import {pokeapi} from "@/api/pokeapi";
  
  export default {
    name :'App',
    
    data() {
      return {
        pokemonData: {},
        pokemonID: '',
      }
    },
    methods: {
      async searchPokemon() {
        try {
          const pokemonToFind= await fetch (`${pokeapi}/${this.pokemonID}`)
          const pokemon = await pokemonToFind.json()
          this.pokemonData = pokemon
          console.log(pokemon)
          return pokemon
        } catch (error){
          alert('pokemon no encontrado')

        }
      }
    }
  }
</script>



<style lang="scss">
  
  @import './tiposPokemon.scss';
  
  .normal {
  background-color: $normal
}
.fire {
  background-color: $fire
}
.water {
  background-color: $water
}
.grass {
  background-color: $grass
}
.electric {
  background-color: $electric
}
.ice {
  background-color: $ice
}
.fighting {
  background-color: $fighting
}
.poison {
  background-color: $poison
}
.ground {
  background-color: $ground
}
.flying {
  background-color: $flying
}
.psychic {
  background-color: $psychic
}
.bug {
  background-color: $bug
}
.rock {
  background-color: $rock
}
.ghost {
  background-color: $ghost
}
.dark {
  background-color: $dark
}
.dragon {
  background-color: $dragon
}
.steel {
  background-color: $steel
}
.fairy {
  background-color: $fairy
}
</style>
