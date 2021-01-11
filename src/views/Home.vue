<template>
  <div class="home border--display">
    <Slide />
  </div>
</template>

<script>
// @ is an alias to /src
import Slide from '@/components/Slide.vue'

export default {
  name: 'Home',
  components: {
    Slide
  }
}
</script>

<style lang="scss" scoped>
.home{
  width: 100%;
  height: 100%;
}
</style>
