<template>
  <div class="info-projects">
    <div class="wrapper" :style="{background : currentData.color}"></div>
  </div>
</template>

<script>
import infos from '@/utils/nameProjectsInfo.json'
export default {
  name : 'PROJECTS',
  computed : {
    getData(){
      return infos
    },
    currentData(){
      return this.getData.find(
        (data) => data.route === this.$route.params.name
      )
    }
  }
}
</script>

<style lang="scss">
.info-projects{
  width: 100%;
  height: auto;
  .wrapper{
    width: 100%;
    height: 100vh;
  }
}
</style>