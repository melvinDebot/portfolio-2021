<template>
  <div class="about">
    <div class="about--text">
      <h2 class="about--title">ABOUT</h2>
      <div class="about--p">
        <p class="reveal-text-about">
          I am Melvin Debot a 21 year old French digital designer and creative
          developer. Currently a 3rd year student in a web school and an
          apprentice at Excenis for more than 1.5 years as a web engineer and
          digital designer. Ready to take the plunge to acquire and develop
          various skills. I aspire to have new perspectives.
        </p>
        <br />
        <p class="reveal-text-about">
          During my apprenticeship, I was able to collaborate with many brands
          such as bolk, madampee or even Tconnect on numerous and varied
          missions such as the creation of a salad vending machine or the
          linking of a video projector connected via a web page.
        </p>
      </div>
      <div class="about--others">
        <div class="about--experience">
          <h3>AWARDS</h3>
          <div class="reveal-text-about">
            <div class="reveal-text-about">
              <h6>2020</h6>
              <p>CSS WINNERS - NOMINEE</p>
            </div>
            <div class="reveal-text-about">
              <h6>2020</h6>
              <p>DESIGN NOMINEES - SITE OF THE DAY</p>
            </div>
            <!-- <div class="reveal-text-about">
              <h6>2020</h6>
              <p>NICEONEILIKE</p>
            </div> -->
          </div>
        </div>
        <div class="about--experience">
          <h3>EXPERIENCES</h3>
          <div class="reveal-text-about">
            <h6>2020 - now</h6>
            <p>Web Engineer at Exceenis</p>
          </div>
          <div class="reveal-text-about">
            <h6>2019 - 2020</h6>
            <p>Freelance Developer Front End at Malt</p>
          </div>
          <div class="reveal-text-about">
            <h6>2018 - 2018</h6>
            <p>Word Press Developer at Transacts</p>
          </div>
          <div class="reveal-text-about">
            <h6>2018 - 2018</h6>
            <p>Project Manager at Hetic</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import gsap, { Power0 } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";
gsap.registerPlugin(ScrollTrigger);
export default {
  name: "About",
  methods: {
    revealAnimation() {
      let allRevealText = document.querySelectorAll(".reveal-text-about");
      gsap
        .timeline({
          scrollTrigger: {
            trigger: ".about",
            start: "10% center",
            end: "55% center",
            scrub: true,
          },
        })
        .fromTo(
          allRevealText,
          0.5,
          {
            y: 10,
            opacity: 0,
            ease: Power0.easeInOut,
            delay: -2,
            stagger: 1,
          },
          {
            y: 0,
            opacity: 1,
            ease: Power0.easeOut,

            stagger: 1,
          }
        );
    },
  },
  mounted() {
    this.revealAnimation();
  },
};
</script>

<style lang="scss" scoped>
.about {
  width: 100%;
  height: 100vh;
  @media (max-width: 500px) {
    height: 200vh;
  }

  .about--text {
    position: relative;
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: space-evenly;
    align-items: center;
    flex-direction: column;
    padding: 0 5.5rem;
    @media (max-width: 500px) {
      padding: 0 10px;
    }
    .about--title {
      position: absolute;
      font-size: 10vw;
      right: -20%;
      top: 44%;
      font-weight: 900;
      transform: rotate(-90deg);
      opacity: 0.4;
    }
    .about--p {
      width: 100%;
      height: auto;
      padding: 10px 0px;
      @media (max-width: 500px) {
        height: 750px;
      }
      p {
        font-size: 1.3rem;
        letter-spacing: 0.01em;
        line-height: 158.5%;
      }
    }
    .about--others {
      width: 100%;
      height: auto;
      display: flex;
      justify-content: flex-start;
      align-items: flex-start;
      @media (max-width: 500px) {
        flex-direction: column;
      }
    }
    .about--experience {
      padding: 15px 0px;
      width: 100%;
      height: auto;
      margin-top: 10px;
      h3 {
        text-align: center;
        margin-bottom: 10px;
        font-size: 1.265rem;
      }
      div {
        margin-top: 25px;
        p {
          margin-top: 3px;
          font-size: 1.3rem;
        }
      }
    }
  }
}
.reveal-text-about-about {
  position: relative;
}
</style>
