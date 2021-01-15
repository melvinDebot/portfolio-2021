<template>
  <div class="container--contact flex">
    <h2 class="container--title">CONTACT</h2>
    <div class="container--text__contact flex">
      <div class="text">
        <div>
          <h2 ref="splitOne">Just Send</h2>
        </div>
        <div>
          <h2 ref="splitTwo">me an <a href="mailto: melvin.debot@hetic.net">email</a></h2>
        </div>
      </div>
      <div class="text">
        <div>
          <h3 ref="splitThree"><a href="https://github.com/melvinDebot?tab=repositories" target="blank">Github</a></h3>
        </div>
        <div>
          <h3 ref="splitFour"><a href="https://www.behance.net/melvindeboa7b2" target="blank">Behance</a></h3>
        </div>
      </div>
      <div class="text ">
        <div>
          <h3 ref="splitFive"><a href="#">Dribble</a></h3>
        </div>
        <div>
          <h3 ref="splitSixt"><a href="https://www.linkedin.com/in/melvin-debot-b22078173/" target="blank">LinkedIn</a></h3>
        </div>
      </div>
    </div>
    <p class="copyright"> © 2021 melvindebot.com</p>
  </div>
</template>

<script>
import { gsap, Power0 } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";
gsap.registerPlugin(ScrollTrigger);
export default {
  name : "Contact",
  methods : {
    SplitTextAnimation(){
      gsap.timeline({
        scrollTrigger : {
          trigger: ".container--contact",
          start: "10% center",
          end: "30% center",
          scrub: true,
        }
      }).timeScale(0.1)
      .fromTo([this.$refs.splitOne, this.$refs.splitTwo],6, 
        {
          y : 200,
          opacity: 0,
          ease : Power0.easeInOut,
          delay : -2
          
        },
        {
          y : 0,
          opacity : 1,
          ease : Power0.easeOut,
          delay : -2
        }
      )
      .fromTo([this.$refs.splitThree, this.$refs.splitFour, this.$refs.splitFive, this.$refs.splitSixt],2, 
        {
          y : 100,
          opacity: 0,
          ease : Power0.easeOut,
          delay: 2
        },
        {
          y : 0,
          opacity : 1,
          ease : Power0.easeOut
        }
      )
    }
  },
  mounted(){
    this.SplitTextAnimation()
  }
}
</script>

<style lang="scss" scoped>
.container--contact{
  width: 100%;
  height: 120vh;
  position: relative;
  overflow-x: hidden;
  @media (max-width: 500px) {
    flex-direction: column;
    height: 120vh;
  }
  .container--title{
    position: absolute;
    font-size: 10vw;
    right: -25%;
    top: 38%;
    font-weight: 900;
    transform: rotate(-90deg);
    opacity: 0.4;
    @media (max-width: 500px) {
      letter-spacing: 5px;
      right: -29%
    }
  }
  .container--text__contact{
    width: 90%;
    height: 40%;
    justify-content: space-evenly;
    @media (max-width: 500px) {
      flex-direction: column;
      height: 120vh;
    }
    .text{
      div {
        position: relative;
        overflow: hidden;
        h2{
          position: absolute;
          font-size: 5vw;
          font-weight: 600;
          position: relative;
          @media (max-width: 500px) {
            font-size: 14vw
          }
          a{
            color: black;
          }
        }
      }
      
      h3{
        font-size: 3.33vw;
        font-weight: 600;
        @media (max-width: 500px) {
            font-size: 12vw
          }
        a{
          color: black;
        }
      }
    }
  }
  .copyright{
    position: absolute;
    text-align: center;
    bottom: 0;
  }
}
</style>