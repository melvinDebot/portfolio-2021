<template>
  <div class="info-projects">
    <div class="wrapper flex" >
      <div class="overlay" :style="{background : currentData.color}" ref="overlay"></div>
        <router-link to="/" class="back flex">
          <img :src="arrow" alt="arrow"/>
          <h3>Back to home</h3>
        </router-link>
      <h2 ref="title">{{ currentData.title }}</h2>
      <div class="indicator_scroll flex">
      <span></span>
      scroll
    </div>
    </div>
    <div class="wrapper flex">
      <div class="screen">
        <div class="screen--buttons flex">
          <div></div>
          <div></div>
          <div></div>
        </div>
        <video width="auto" height="auto" autoplay>
          <source :src="getVideoPath(currentData.video)" type="video/mp4">
        </video>
      </div>
      <div class="infos">
        <p class="infos--text">{{ currentData.text }}</p>
        <div class="infos--plus">
          <h4>Years</h4>
          <p>{{ currentData.year }}</p>
        </div>
        <div class="infos--plus">
          <h4>Clients</h4>
          <p>{{ currentData.client }}</p>
        </div>
        <div class="infos--plus">
          <h4>Missions</h4>
          <p>{{ currentData.text_mission }}</p>
        </div>
        <a class="info--button" v-if="currentData.display" href="#" :style="{background : currentData.color}">
          Voir le site
        </a>
      </div>
    </div>
  </div>
</template>

<script>
import infos from '@/utils/nameProjectsInfo.json'
import gsap, {Power3} from 'gsap'
import arrow from '@/assets/arrow.svg'
export default {
  name : 'PROJECTS',
  data : function(){
    return {
      arrow : arrow,
      displayButton : false
    }
  },
  created() {
    this.getData()
  },
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
      gsap.fromTo(this.$refs.overlay, 1, 
        {
          height : '0vh',
          bottom: -100
        },
        {
          height : '100vh',
          bottom: 0
        }
      )
      gsap.fromTo(this.$refs.title, 1, 
        {
          y : 0,
          opacity : 0,
          ease : Power3.easeInOut,
          delay: 5
        },
        {
          y: 50,
          opacity: 1,
          ease : Power3.easeOut,
          delay: 1
        }
      )
    },
    getVideoPath(video){
      return require(`@/assets/videos/${video}.mp4`)
    },
    clickedRoute(routeName){
      window.scrollTo(0, 0)
      this.$router.push(routeName)
    },
    buttonShow(show){
      if(show === 'private'){
        this.displayButton = false
      } else{
        this.displayButton = true
      }
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
    position: relative;
    .overlay{
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100vh;
      background: black;
    }
    &:nth-child(2){
      height: auto;
      padding: 50px 0px;
      justify-content: space-around;
      @media (max-width: 500px) {
        flex-direction: column;
      }
    }
    .back{
      position: absolute;
      width: 195px;
      justify-content: space-between;
      top: 25px;
      left: 25px;
      color: white;
      text-decoration: none;
      img{
        width: 50px;
      }
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
    .screen{
      width:auto;
      height: auto;
      @media (max-width: 500px) {
        width: 90%;
      }
      video{
        max-width: 650px;
        @media (max-width: 500px) {
          width: 90%;
        }
      }
      .screen--buttons{
        width: 100%;
        height: 25px;
        background: #E1E4EB;
        justify-content: flex-start;
        padding-left: 10px;
        div{
          width: 10px;
          margin-right: 4px;
          height: 10px;
          border-radius: 50%;
          &:nth-child(1){
            background: #FF796F;
          }
          &:nth-child(2){
            background: #FFD171;
          }
          &:nth-child(3){
            background: #64C255;
          }
        }
      }
    }
    .infos{
      width: 50%;
      height: 70vh;
      padding: 0px 10px;
      @media (max-width: 500px) {
        margin-top: 30px;
        width: 90%;
        height: 94vh;
      }
      .infos--text{
        margin-top: 30px;
        font-weight: normal;
        font-size: 18px;
        line-height: 142.5%;
      }
      .infos--plus{
        margin-top: 30px;
        h4{
          font-weight: bold;
          font-size: 18px;
          line-height: 22px;
        }
        p{
          margin-top: 8px;
          font-weight: normal;
          font-size: 18px;
          line-height: 142.5%;
          margin-bottom: 8px;
        }
      }
      .info--button{
        text-decoration: none;
        width: 150px;
        height: 50px;
        color: white;
        border: none;
        margin-top:30px;
        font-size: 30px;
      }
    }
  }
  .next--banner{
    width: 100%;
    height: 100px;
    color: white;
  }
}
</style>