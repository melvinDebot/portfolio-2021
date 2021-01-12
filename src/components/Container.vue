<template>
  <div class="container display">
    <div class="container--text">
      <h2
        v-for="(title, index) in projects"
        :key="index"
        :class="title.class_position"
        @click="$router.push(title.link)"
      >
        {{ title.name }}
      </h2>
    </div>
  </div>
</template>

<script>
import projects from '@/utils/nameProjects.json'
export default {
  data : function(){
    return {
      projects : projects
    }
  }
}
</script>

<style lang="scss" scoped>
.container{
  width: 100%;
  height: 80vh;
  .right{
    float: right;
    margin-top: 30px;
  }
}
</style>