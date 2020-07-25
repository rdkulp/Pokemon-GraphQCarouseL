<template>
  <div id="pokemon-grid">
    <h2 id="counter">Pokémon caught: {{ counter }}</h2>
    <span id="caught">
      <h1 v-for="n in 6">You caught 'em all!</h1>
    </span>
    <div class="poke-grid" v-for="(pokemon, index) in pokemons" :key="pokemon.id">
      <img
        class="pokemon"
        :src="pokemon.image"
        :id="pokemon.id"
        :alt="pokemon.name"
        v-model="counter"
        @click="counter += 1; catchEm(index, counter);"
      />
    </div>
  </div>
</template>

<script>
import gql from "graphql-tag";
export default {
  apollo: {
    pokemons: gql`
      query getPokemon {
        pokemons(first: 10) {
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
    catchEm: function (index, counter) {
      if (counter < 10) {
        this.pokemons.splice(index, 1);
      } else {
        this.pokemons.splice(index, 1);
        const winner = document.getElementById("caught");
        winner.style.visibility = "visible";
      }
    },
  },
};
</script>

<style>
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
  top: 10vw;
  left: 5px;
  opacity: 1;
}
#pokemon-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
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

/* Caught 'em All */
span h1 {
  color: goldenrod;
  animation: flicker 3s infinite;
}
@keyframes flicker {
  0% {
    opacity: 1;
  }
  50% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}
span h1:nth-child(1) {
  color: slategray;
  animation: flicker 2500ms infinite;
}
span h1:nth-child(2) {
  color: slateblue;
  animation: flicker 2s infinite;
}
span h1:nth-child(3) {
  color: cornflowerblue;
  animation: flicker 1500ms infinite;
}
span h1:nth-child(4) {
  color: teal;
  animation: flicker 1s infinite;
}
span h1:nth-child(5) {
  color: tomato;
  animation: flicker 500ms infinite;
}
span h1:nth-child(6) {
  color: goldenrod;
}
#caught {
  visibility: hidden;
  position: absolute;
  top: 25%;
  left: 0;
  font-size: 3vw;
  width: 100%;
  text-transform: uppercase;
  font-family: "futura";
  overflow: hidden;
  line-height: 6rem;
}
</style>