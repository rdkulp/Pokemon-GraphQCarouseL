<template>
  <div id="lights">
    <img src="~/assets/red-pokeball.svg" id="red" alt="red-pokemon-ball-fades" />
    <img src="~/assets/yellow-pokeball.svg" id="yellow" alt="yellow-pokemon-ball-fades" />
    <img src="~/assets/green-pokeball.svg" id="green" alt="green-pokemon-ball-fades" />
  </div>
</template>

<style scoped>
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

@keyframes fadeout {
  0% {
    opacity: 1;
  }
  100% {
    opacity: 0;
  }
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
</style>