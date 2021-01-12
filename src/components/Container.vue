<template>
  <div class="container">
    <div class="container--text display">
      <div 
        class="text"
        v-for="(title, index) in projects"
        :key="index"
        :class="title.class_position"
        @click="$router.push(title.link)"
      >
        <h2>{{ title.name }}</h2>
        <h5>{{ title.subtitle }}</h5>
      </div>
    </div>
  </div>
</template>

<script>
import projects from '@/utils/nameProjects.json'
import gsap from 'gsap'
import { ScrollTrigger } from "gsap/ScrollTrigger";

gsap.registerPlugin(ScrollTrigger);
export default {
  data : function(){
    return {
      projects : projects
    }
  },
  methods : {
    scrollAnimation(){
      gsap.timeline({
        scrollTrigger : {
          trigger: ".container--text",
          start: "top center",
          end: "bottom bottom",
          markers: true,
          scrub: true,
        }
      })
      .to('.left', 1, {x: 100})
      .to('.right', 1, {x: -100, delay : -1})
    }
  },
  mounted(){
    this.scrollAnimation()
  }
}
</script>

<style lang="scss" scoped>
.container{
  width: 100%;
  height: 100vh;
  padding: 50px 0px;
  .container--text{
    width: 100%;
    height: 100%;
    display: flex;
    flex-wrap: nowrap;
    flex-direction: column;
    justify-content: space-around;
  }
  h2{
    font-weight: 600;
    font-size: 96px;
  }
  .right {
    float: right;
    align-self: flex-end;
  }
  .text{
    cursor: pointer;
    overflow: hidden;
    position: relative;
  }
}
</style>