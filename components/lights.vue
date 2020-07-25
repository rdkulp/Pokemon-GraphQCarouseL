<template>
  <div id="lights">
    <img src="~/assets/red-pokeball.svg" id="red" alt="red-pokemon-ball-fades" />
    <img src="~/assets/yellow-pokeball.svg" id="yellow" alt="yellow-pokemon-ball-fades" />
    <img src="~/assets/green-pokeball.svg" id="green" alt="green-pokemon-ball-fades" />
    <h1 id="catch">Click 'em All!</h1>
  </div>
</template>

<style scoped>
h1 {
  font-family: "futura";
  text-transform: uppercase;
}
#lights {
  position: relative;
  display: flex;
  justify-content: center;
}
#lights img {
  width: 100px;
  height: 100px;
  margin-left: 30px;
  opacity: 0;
}

#red {
  animation-name: fadeout;
  animation-delay: 1500ms;
  animation-duration: 2s;
}

#yellow {
  animation-name: fadeout;
  animation-delay: 3s;
  animation-duration: 2s;
}

#green {
  animation-name: fadeout;
  animation-delay: 4500ms;
  animation-duration: 2s;
}

#catch {
  animation-name: fadeout;
  animation-timing-function: ease;
  animation-delay: 5500ms;
  animation-duration: 3s;
  opacity: 0;
  position: absolute;
  width: 100%;
  top: 100px;
  font-size: 3.5rem;
}

@keyframes fadeout {
  0% {
    opacity: 1;
  }
  100% {
    opacity: 0;
  }
}
</style>