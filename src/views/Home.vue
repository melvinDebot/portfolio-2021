<template>
  <div class="home border--display">
    <Header />
    <Container />
    <ContainerTarifs />
    <Contact />
  </div>
</template>

<script>
// @ is an alias to /src
import Header from '@/components/Header.vue'
import Container from '@/components/Container.vue'
import ContainerTarifs from '@/components/ContainerTarifs.vue'
import Contact from '@/components/Contact.vue'

export default {
  name: 'Home',
  components: {
    Header,
    Container,
    ContainerTarifs,
    Contact
  }
}
</script>

<style lang="scss" scoped>
.home{
  width: 100%;
  height: auto;
}
</style>
