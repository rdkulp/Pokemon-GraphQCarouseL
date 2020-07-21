<template>
  <div class="container">
    <div>
      <Logo />
    </div>
    <Carousel />
  </div>
</template>

<script>
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

ul {
  display: flex;
  flex-direction: column-reverse;
}

.links {
  padding-top: 15px;
}
</style>
