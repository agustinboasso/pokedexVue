<template>
  <header class="header">
    <label for="">
      escreva o nome do pokémon ou seu id
      <input type="text" name="" id="">
      <button>Busca tu pokemon</button>
    </label>
  </header>
  
  <main>
    <section class="pokemonCard">
      <div class="nameImage">
        <h1 class="pokemonName">pikachu</h1>
        <img src="" alt="pikachu">

      </div>
      <ul class="type">
      <h2>Type</h2>
        <li>
          <span>Electric</span>
        </li>
      </ul>
      <ul class="stats">
        <h2>stats</h2>
        <li>
          <span></span>
        </li>
      </ul>
    </section>
  </main>
  
</template>


<script>
  import {pokeapi} from "@/api/pokeapi";
  export default{
    name :'App',
    
    data(){
      return{
        pokemonData:{},
        pokemonID:'',
      }
    },
    methods: {
      async searchPokemon() {
        try {
          const pokemonABuscar = await fetch (`${pokeapi}/${this.pokemonID}`)
          const pokemon = await pokemonABuscar.json()
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

<script>




</script>

<style lang="scss">

</style>
