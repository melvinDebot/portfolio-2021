<template>
  <div class="info-projects">
    <div class="wrapper flex" :style="{background : currentData.color}">
      <div class="back">
        <h3>Retour</h3>
      </div>
      <h2 ref="title">{{ currentData.title }}</h2>
      <div class="indicator_scroll flex">
      <span></span>
      scroll
    </div>
    </div>
    <div class="wrapper"></div>
  </div>
</template>

<script>
import infos from '@/utils/nameProjectsInfo.json'
import gsap, {Power3} from 'gsap'
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
  },
  methods : {
    animationWrapper(){
      gsap.fromTo(this.$refs.title, 1, 
        {
          y : 100,
          opacity : 0,
          ease : Power3.easeInOut
        },
        {
          y: 0,
          opacity: 1,
          ease : Power3.easeOut
        }
      )
    }
  },
  mounted(){
    window.scrollTo(0, 0)
    this.animationWrapper()
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
    .back{
      position: absolute;
      top: 0;
      left: 0;
    }
    h2{
      font-size: 8.6vw;
      color: white;
      @media (max-width: 500px) {
        font-size: 10.6vw;
      }
    }
    .indicator_scroll{
      position: absolute;
      flex-direction: column;
      justify-content: space-around;
      bottom: 0;
      color: white;
      width: 89px;
        height: 107px;
      span{
        width: 78px;
        height: 1px;
        border: 1px solid white;
        transform: rotate(90deg);
        animation: scrollAnimation 2s infinite cubic-bezier(0, 1, 1, 1);
      }
    }
  }
}
</style>