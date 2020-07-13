<template>
  <div class="pokemon-carousel-container">
    <ul class="pokemon-carousel">
      <li class="poke-list" v-for="pokemon in pokemons" :key="pokemon.id">
        <img :src="pokemon.image" />
      </li>
    </ul>
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
.pokemon-carousel-container {
  position: relative;
  width: 50%;
  margin: auto;
}

.pokemon-carousel {
  position: relative;
  margin-top: 2rem;
  height: 50vw;
}

.pokemon-carousel li img {
  width: 100px;
}

.pokemon-carousel li {
  position: absolute;
  left: 50%;
  top: 0;
  width: 30%;
  height: 100%;
  padding: 0;
  cursor: pointer;
  transition: transform 1.3s cubic-bezier(0.19, 1, 0.22, 1);
  z-index: 1;
}

.pokemon-carousel li:nth-child(1) {
  z-index: 4;
  transform: translateX(-50%) scale(1) translate3d(0, 40%, 0);
}

.pokemon-carousel li:nth-child(2) {
  z-index: 3;
  transform: translateX(-50%) scale(0.875) translate3d(240%, 30%, 0);
}

.pokemon-carousel li:nth-child(8) {
  z-index: 3;
  transform: translateX(-50%) scale(0.875) translate3d(-240%, 30%, 0);
}

.pokemon-carousel li:nth-child(3) {
  z-index: 2;
  transform: translateX(-50%) scale(0.75) translate3d(300%, 10%, 0);
}

.pokemon-carousel li:nth-child(7) {
  z-index: 2;
  transform: translateX(-50%) scale(0.75) translate3d(-300%, 10%, 0);
}

.pokemon-carousel li:nth-child(4) {
  z-index: 1;
  transform: translateX(-50%) scale(0.625) translate3d(240%, -10%, 0);
}

.pokemon-carousel li:nth-child(6) {
  z-index: 1;
  transform: translateX(-50%) scale(0.625) translate3d(-240%, -10%, 0);
}

.pokemon-carousel li:nth-child(5) {
  z-index: 0;
  transform: translateX(-50%) scale(0.5) translate3d(0, -30%, 0);
}

.poke-list {
  list-style: none;
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont,
    "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  color: white;
  font-size: 3rem;
  font-weight: 500;
  display: block;
}
</style>