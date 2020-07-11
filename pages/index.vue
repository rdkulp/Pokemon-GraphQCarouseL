<template>
  <div class="container">
    <div>
      <Logo />
    </div>
    <br />
    <div class="pokemon-carousel">
      <ul>
        <li class="poke-list" v-for="pokemon in pokemons" :key="pokemon.id">{{ pokemon.name }}</li>
      </ul>
    </div>
  </div>
</template>

<script>
import gql from "graphql-tag";
export default {
  apollo: {
    pokemons: gql`
      query getPokemon {
        pokemons(first: 8) {
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
    `
  }
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
}

.pokemon-carousel {
  display: block;
  width: 100%;
  position: relative;
  margin-top: 5rem;
}

.poke-list {
  list-style: none;
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont,
    "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  color: white;
  font-size: 3rem;
  font-weight: 500;
}

.links {
  padding-top: 15px;
}
</style>
