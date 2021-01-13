<template>
  <div class="container">
    <div class="container--text">
      <h2 class="container--title">WORKS</h2>
      <div 
        class="text"
        v-for="(title, index) in projects"
        :key="index"
        :class="title.class_position"
        @click="clicked(title.link)"
      >
        <h2>{{ title.name }}</h2>
        <h5>{{ title.subtitle }}</h5>
      </div>
    </div>
  </div>
</template>

<script>
import projects from '@/utils/nameProjects.json'
import gsap, {Power1} from 'gsap'
import { ScrollTrigger } from "gsap/ScrollTrigger";

gsap.registerPlugin(ScrollTrigger);
export default {
  name: 'Projects',
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
          end: "bottom center",
          markers: true,
          scrub: true,
        }
      })
      .to('.left', 1, {x: '100%', ease : Power1.easeInOut})
      .to('.right', 1, {x: '-200%', delay : -1, ease : Power1.easeInOut})
    },
    clicked(link){
      this.$router.push(link)
      
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
  height: 110vh;
  padding: 50px 0px;
  overflow-x: hidden;
  .container--text{
    width: 100%;
    height: 100%;
    display: flex;
    flex-wrap: nowrap;
    flex-direction: column;
    justify-content: space-around;
    position: relative;
  }
  .container--title{
    position: absolute;
    font-size: 10vw;
    right: -20%;
    top: 44%;
    font-weight: 900;
    transform: rotate(-90deg);
    opacity: 0.4;
  }
  .right {
    float: right;
    align-self: flex-end;
  }
  .text{
    height: auto;
    cursor: pointer;
    overflow: hidden;
    position: relative;
    width: fit-content;
    h2{
    font-weight: 600;
      font-size: 8.6vw;
      @media (max-width: 500px) {
        font-size: 12.6vw;
      }
    }
    h5{
      font-weight: 400;
      position: absolute;
      bottom: 0;
      left: 0;
      font-size: 1.25vw;
      animation: move 4s infinite normal 0s linear;
      text-align: initial;
      white-space: nowrap;
      color: #16BF15;
      @media (max-width: 500px) {
        margin-top: 20px;
        font-size: 2.5vw;
      }
    }
  }
  .overlay{
      position: absolute;
      width: 0%;
      height: 0vh;
      z-index: 100;
      background: lightblue;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
  }
}
@keyframes move {
  0%{
    left: -10%;
  }
  100%{
    left: 100%;
  }
}
</style>