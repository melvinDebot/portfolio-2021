<template>
  <div class="about">
    <div class="about--text">
      <h2 class="about--title">ABOUT</h2>
      <div class="about--p">
        <p>
          I am Melvin Debot a 21 year old French digital designer and creative
          developer. Currently a 3rd year student in a web school and an
          apprentice at Excenis for more than 1.5 years as a web engineer and
          digital designer. Ready to take the plunge to acquire and develop
          various skills. I aspire to have new perspectives.
        </p>
        <br />
        <p>
          During my apprenticeship, I was able to collaborate with many brands
          such as bolk, madampee or even Tconnect on numerous and varied
          missions such as the creation of a salad vending machine or the
          linking of a video projector connected via a web page.
        </p>
      </div>
      <div class="about--others">
        <div class="about--experience">
          <h3>REFERENCES</h3>
          <div>
            <h6>2020</h6>
            <p>CSS WINNERS</p>
          </div>
        </div>
        <div class="about--experience">
          <h3>EXPERIENCES</h3>
          <div>
            <h6>2020 - now</h6>
            <p>Ingénieur web at Exceenis</p>
          </div>
          <div>
            <h6>2019 - 2020</h6>
            <p>Freelance Developper Front End at Malt</p>
          </div>
          <div>
            <h6>2018 - 2018</h6>
            <p>Developer Word Press at Transacts</p>
          </div>
          <div>
            <h6>2018 - 2018</h6>
            <p>Chef de projet at Hetic</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import gsap from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";
gsap.registerPlugin(ScrollTrigger);
export default {
  name: "About",
  methods: {},
  mounted() {
    this.scrollContainer();
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
      justify-content: start;
      align-items: flex-start;
      @media (max-width: 500px) {
        flex-direction: column;
      }
    }
    .about--experience {
      padding: 10px 0px;
      width: 100%;
      height: auto;
      margin-top: 10px;
      h3 {
        text-align: center;
        margin-bottom: 10px;
        font-size: 1.265rem;
      }
      div {
        margin-top: 20px;
        p {
          margin-top: 3px;
          font-size: 1.3rem;
        }
      }
    }
  }
}
</style>
