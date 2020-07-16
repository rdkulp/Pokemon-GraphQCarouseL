<template>
  <div class="pokemon-carousel-container">
    <ul class="pokemon-carousel">
      
      <li v-for="pokemon in pokemons" :key="pokemon.id">
        <img :src="pokemon.image" />
        <h2> {{ pokemon.name }} </h2>
        <p> {{ pokemon.type }} </p>
      </li>
    
    </ul>
    <div class="control">
      <span class="left arrow" v-on:click="rotate(pokemons)"><</span>
      <span class="right arrow" v-on:click="rotateLeft(pokemons)">></span>
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
  },
  methods: {
    rotate: function (a) {
      return a.unshift(a.pop());
    },
    rotateLeft: function (a) {
      return a.push(a.shift());
    }
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
  cursor: help;
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
  list-style-type: none;
}

.control {
  position: sticky;
  bottom: 0;
  display: flex;
  width: 50%;
  margin-left: auto;
  margin-right: auto;
  justify-content: space-between;
}

.left, .right {
  font-size: 200px;
  transition: background-position 275ms ease;
  overflow: hidden;
  cursor: pointer;
}

.left {
  background: linear-gradient(to right, royalblue, royalblue 50%, midnightblue 50%);
  position: relative;
  display: inline-block;
  background-clip: text;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-size: 200% 100%;
  background-position: 0%;
}

.right {
  background: linear-gradient(to left, royalblue, royalblue 50%, midnightblue 50%);
  position: relative;
  display: inline-block;
  background-clip: text;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-size: 200% 100%;
  background-position: 100%;
}

/* .arrow {
  position: relative;
  display: inline-block;
  background-clip: text;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-size: 200% 100%;
  background-position: 100%;
} */
.right:hover {
  background-position: 0 100%;
}

.left:hover {
  background-position: 100% 0%;
}

.pokemon-carousel li:nth-child(1) {
  z-index: 4;
  transform: translateX(-50%) scale(1) translate3d(0, 40%, 0);
}

.pokemon-carousel li:nth-child(1), .pokemon-carousel li:nth-child(8) {
  animation: fadeIn ease 1s;
  -webkit-animation: fadeIn ease 1s;
  -moz-animation: fadeIn ease 1s;
  -o-animation: fadeIn ease 1s;
  -ms-animation: fadeIn ease 1s;
}

@keyframes fadeIn {
0% {opacity:0;}
100% {opacity:1;}
}

.pokemon-carousel li:nth-child(2) {
  z-index: 3;
  transform: translateX(-50%) scale(0.875) translate3d(150%, 30%, 0);
}

.pokemon-carousel li:nth-child(8) {
  z-index: 3;
  transform: translateX(-50%) scale(0.875) translate3d(-150%, 30%, 0);
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

.hover-card {
  width: 50%;
  height: auto;
  padding: 1rem;
  background-color: royalblue;
  margin-top: -25rem;
  position: absolute;
  font-family: "futura";
  font-size: 1rem;
  font-weight: 600;
  color: white;
  align-content: center;
}
</style>