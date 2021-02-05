<template>
  <div class="container">
    <div class="container--text">
      <h2 class="container--title">WORKS</h2>
      <div
        class="text--primary"
        v-for="(title, index) in projects"
        :key="index"
        :class="title.class_position"
        @click="clicked(title.link)"
      >
        <div class="text">
          <h2>{{ title.name }}</h2>
          <h5>{{ title.subtitle }}</h5>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import projects from "@/utils/nameProjects.json";
import gsap, { Power1 } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";
gsap.registerPlugin(ScrollTrigger);
export default {
  name: "Projects",
  data: function () {
    return {
      projects: projects,
    };
  },
  methods: {
    scrollAnimation() {
      gsap
        .timeline({
          scrollTrigger: {
            trigger: ".container--text",
            start: "top center",
            end: "170% center",
            scrub: true,
          },
        })
        .timeScale(0.9)
        .to(".left", 5.5, { x: "100%", ease: Power1.easeInOut })
        .to(".right", 5.5, { x: "-190%", delay: -5.5, ease: Power1.easeInOut });
    },
    clicked(link) {
      this.$router.push(link);
    },
    currentImg(img) {
      return require(`@/assets/images/${img}.png`);
    },
    animatedImg() {
      let arrayImg = document.querySelectorAll(".block--img");
      window.addEventListener("mousemove", (e) => {
        let left = e.pageX - 190;
        arrayImg.forEach((img) => {
          img.style.left = left + "px";
        });
      });
    },
  },
  mounted() {
    this.scrollAnimation();
  },
};
</script>

<style lang="scss" scoped>
.block--img {
  position: absolute;
  left: 0px;
  top: -20px;
  width: 316px;
  height: 316px;
  display: none;
  transition: all 0.1s linear;
  -webkit-transition: all 0.1s linear;
}
.container {
  width: 100%;
  height: 150vh;
  @media (max-width: 500px) {
    height: 100vh;
  }
  padding: 50px 0px;
  overflow-x: hidden;
  .container--text {
    width: 100%;
    height: 100%;
    display: flex;
    flex-wrap: nowrap;
    flex-direction: column;
    justify-content: space-around;
    position: relative;
  }
  .container--title {
    position: absolute;
    font-size: 10vw;
    right: -20%;
    top: 44%;
    font-weight: 900;
    transform: rotate(-90deg);
    opacity: 0.4;
    @media (max-width: 500px) {
      letter-spacing: 5px;
      right: -23%;
    }
  }
  .right {
    float: right;
    align-self: flex-end;
  }
  .text--primary {
    width: fit-content;
    .text {
      height: auto;
      cursor: pointer;
      overflow: hidden;
      position: relative;
      width: fit-content;
      transition: all 1s ease-out;
      -webkit-transition: all 2s ease-in-out;

      h2 {
        font-weight: 800;
        font-size: 8.6vw;
        transition: all 1s ease-out;
        -webkit-transition: all 0.5s ease-in-out;
        @media (max-width: 500px) {
          font-size: 12.6vw;
        }
      }
      h5 {
        font-weight: 400;
        position: absolute;
        bottom: 0;
        left: 0;
        font-size: 1.25vw;
        animation: move 4s infinite normal 0s linear;
        text-align: initial;
        white-space: nowrap;
        color: #16bf15;
        @media (max-width: 500px) {
          margin-top: 20px;
          font-size: 2.5vw;
        }
      }
    }
    &:hover {
      h2 {
        color: black;
        -webkit-text-fill-color: var(
          --white-color
        ); /* Will override color (regardless of order) */
        -webkit-text-stroke-width: 1px;
        -webkit-text-stroke-color: var(--black-color);
      }
      .block--img {
        display: block;
      }
    }
  }

  .overlay {
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
  0% {
    left: -10%;
  }
  100% {
    left: 100%;
  }
}
</style>
