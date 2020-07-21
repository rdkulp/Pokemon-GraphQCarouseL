<template>
  <div class="ball-box">
    <svg viewBox="0 0 500 400">
      <circle class="ball" cx="80" cy="80" r="80" />
    </svg>
  </div>
</template>

<script>
</script>

<style scoped>
.ball-box {
  display: flex;
  align-content: flex-start;
  width: 80%;
  margin: auto;
}

.ball {
  fill: darkslateblue;
}

svg {
  width: 100px;
  height: 100px;
}
</style>