<template>
  <div class="header">
    <img class="logo" src="~/assets/logo.png" />
  </div>
</template>

<style>
.header {
  width: 100%;
  background-color: darkslateblue;
  height: 9vw;
  display: flex;
  justify-content: center;
  align-items: center;
}
.logo {
  animation: 1s appear;
  position: relative;
  width: 7.5%;
}

@keyframes appear {
  0% {
    opacity: 0;
  }
}
</style>

