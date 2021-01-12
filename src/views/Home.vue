<template>
  <div class="home border--display">
    <Header />
    <Container />
  </div>
</template>

<script>
// @ is an alias to /src
import Header from '@/components/Header.vue'
import Container from '@/components/Container.vue'

export default {
  name: 'Home',
  components: {
    Header,
    Container
  }
}
</script>

<style lang="scss" scoped>
.home{
  width: 100%;
  height: auto;
}
</style>
