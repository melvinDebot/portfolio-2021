<template>
  <div class="home border--display">
    <Header />
  </div>
</template>

<script>
// @ is an alias to /src
import Header from '@/components/Header.vue'

export default {
  name: 'Home',
  components: {
    Header,
  }
}
</script>

<style lang="scss" scoped>
.home{
  width: 100%;
  height: auto;
}
</style>
