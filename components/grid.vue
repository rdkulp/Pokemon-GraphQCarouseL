<template>
  <div id="pokemon-grid">
    <h2 id="counter">Pokémon caught: {{ counter }}</h2>
    <div class="poke-grid" v-for="(pokemon, index) in pokemons" :key="pokemon.id">
      <img
        class="poke-ball"
        :src="pokemon.image"
        :id="pokemon.id"
        :alt="pokemon.name"
        v-model="counter"
        @click="counter += 1; catchEm(index);"
      />
      <h2>{{ pokemon.name }}</h2>
    </div>
  </div>
</template>

<script>
import gql from "graphql-tag";
export default {
  apollo: {
    pokemons: gql`
      query getPokemon {
        pokemons(first: 120) {
          id
          name
          weight {
            maximum
          }
          types
          weaknesses
          fleeRate
          image
        }
      }
    `,
  },
  data() {
    return {
      counter: 0,
    };
  },
  methods: {
    catchEm: function (index) {
      this.pokemons.splice(index, 1);
    },
  },
};
</script>

<style>
/* Sample `apply` at-rules with Tailwind CSS
.container {
@apply min-h-screen flex justify-center items-center text-center mx-auto;
}
*/
.container {
  margin: 0 auto;
  min-height: 100vh;
  justify-content: center;
  align-items: center;
  text-align: center;
  width: 100%;
}
#counter {
  position: fixed;
  top: 0;
  left: 5px;
}
#pokemon-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-column-gap: 4px;
  grid-row-gap: 4px;
  width: 80%;
  margin-top: 4rem;
  margin-left: 10%;
  margin-right: 10%;
}
#pokemon-grid div img {
  height: 100px;
  margin: 2rem;
  align-items: center;
}
#pokemon-grid div img:hover {
  transform: translate(0, -2.5%);
  cursor: url("/assets/poke-ball.png");
}
.poke-ball {
  cursor: url("/assets/poke-ball.png");
}
.poke-grid {
  margin-top: 2rem;
}
ul {
  display: flex;
  flex-direction: column-reverse;
}
.poke-list {
  list-style: none;
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont,
    "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  color: slateblue;
  font-size: 3rem;
  font-weight: 500;
  display: block;
}
.links {
  padding-top: 15px;
}
@media only screen and (max-width: 649px) {
  #pokemon-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    grid-column-gap: 4px;
    grid-row-gap: 4px;
    width: 80%;
    margin-top: 4rem;
    margin-left: 10%;
    margin-right: 10%;
  }
}
</style>