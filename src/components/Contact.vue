<template>
  <div class="container--contact display">
    <h2 class="container--title">CONTACT</h2>
  </div>
</template>

<script>
export default {
  name : "Contact"
}
</script>

<style lang="scss" scoped>
.container--contact{
  width: 100%;
  height: 100vh;
  position: relative;
  overflow-x: hidden;
  .container--title{
    position: absolute;
    font-size: 10vw;
    right: -25%;
    top: 38%;
    font-weight: 900;
    transform: rotate(-90deg);
    opacity: 0.4;
  }
}
</style>