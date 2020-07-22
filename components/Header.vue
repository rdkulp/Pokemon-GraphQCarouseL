<template>
  <div class="header">
    <nav class="nav-left">
      <nuxt-link to="/">Carousel</nuxt-link>
      <nuxt-link to="/grid">Grid</nuxt-link>
    </nav>
    <img class="logo" src="~/assets/logo.png" alt="poke-ball" />
  </div>
</template>

<style>
.header {
  width: 100%;
  background-color: darkslateblue;
  height: 9vw;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.logo {
  animation: 1s appear;
  position: relative;
  width: 7.5%;
  margin-right: 50%;
}
.nav-left a {
  font-family: "futura";
  color: white;
  font-size: 3rem;
  text-decoration: none;
  margin-left: 10%;
}
.nav-left {
  display: flex;
  justify-content: flex-start;
  width: 50%;
}
@media only screen and (max-width: 649px) {
  .header {
    flex-direction: row-reverse;
    justify-content: space-between;
  }
  .logo {
    margin-right: 20%;
  }
  .nav {
    font-size: 1rem;
  }
  .nav-left {
    width: 60%;
  }
  .nav-left a {
    margin: auto;
    margin-right: 20px;
    font-size: 1rem;
  }
  .logo {
    margin: auto;
    margin-left: 10px;
  }
}
@keyframes appear {
  0% {
    opacity: 0;
  }
}
</style>

