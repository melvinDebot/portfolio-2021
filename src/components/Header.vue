<template>
  <div class="header">
    <button class="header--button flex" @click="toggleMode">
      <img :src="currentImage()" alt="" />
    </button>
    <div class="subtitle flex">
      <h3 ref="nameUser">MELVIN DEBOT</h3>
    </div>
    <div class="title">
      <div class="title--text">
        <span class="reveal-span">AVAILABLE</span> <br />
        <span class="reveal-span">FOR EXCITING</span><br />
        <span class="reveal-span">FREELANCE</span> <br />
        <span class="reveal-span">PROJECTS</span>
      </div>
      <h2 class="one" ref="textOne">CREATIVE</h2>
      <h2 class="two" ref="textTwo">DEVELOPER</h2>
    </div>
    <div class="indicator_scroll flex">
      <span></span>
      scroll
    </div>
  </div>
</template>

<script>
import gsap, { Power3 } from "gsap";
import moonIcon from "../assets/moon.svg";
import moonDarkIcon from "../assets/moon--dark.svg";
export default {
  name: "Header",
  data: function () {
    return {
      moonIcon: moonIcon,
      moonDarkIcon: moonDarkIcon,
      swicthMode: true,
    };
  },
  methods: {
    animationHeader() {
      let allSpanText = document.querySelectorAll(".reveal-span");
      gsap.fromTo(
        this.$refs.textOne,
        1,
        { x: "30%", opacity: 0, ease: Power3.easeInOut },
        { x: "0%", opacity: 1, ease: Power3.easeOut }
      );
      gsap.fromTo(
        this.$refs.textTwo,
        1,
        { x: "-30%", opacity: 0, ease: Power3.easeInOut },
        { x: "0%", opacity: 1, ease: Power3.easeOut }
      );
      gsap.fromTo(
        this.$refs.nameUser,
        1,
        {
          y: -10,
          opacity: 0,
          ease: Power3.easeIn,
        },
        {
          y: 0,
          opacity: 1,
          ease: Power3.easeIn,
        }
      );
      gsap.fromTo(
        allSpanText,
        1,
        {
          y: -10,
          opacity: 0,
          ease: Power3.easeIn,
        },
        {
          y: 0,
          opacity: 1,
          ease: Power3.easeIn,
          stagger: 0.3,
        }
      );
    },
    toggleMode() {
      this.swicthMode = !this.swicthMode;
      var element = document.body;
      if (this.swicthMode == true) {
        element.setAttribute("data-theme", "dark");
      } else if (this.swicthMode == false) {
        element.setAttribute("data-theme", "light");
      }

    },
    currentImage() {
      return this.swicthMode ? moonDarkIcon : moonIcon;
    },
  },
  created() {},
  mounted() {
    this.toggleMode();
    this.animationHeader();
  },
};
</script>

<style lang="scss" scoped>
@import url("/styles/header.scss");
.header {
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-direction: column;
  overflow-x: hidden;
  padding: 75px 0px;
  position: relative;
  .header--button {
    position: absolute;
    top: 72px;
    right: 298px;
    background: none;
    border: none;
    outline: none;
    @media (max-width: 500px) {
      top: 72px;
      right: 29px;
    }
  }
  h3 {
    opacity: 1;
    font-weight: 300;
    text-align: center;
  }
  .title {
    width: 100%;
    height: 80%;
    position: relative;
    padding: 20px 0px;
    .title--text {
      height: auto;
      padding: 5px 0px;
      position: absolute;
      top: 0;
      left: 8px;
      font-size: 20px;
      @media (max-width: 500px) {
        font-size: 11px;
        top: 0;
      }
    }
    @media (max-width: 500px) {
      height: 30%;
    }
    h2 {
      font-size: 17vw;
      font-weight: 900;
    }
    .one {
      position: absolute;
      top: 0;
      // right: -200px;
      right: -200px;
      @media (max-width: 500px) {
        font-size: 18vw;
        right: -85px;
      }
    }
    .two {
      position: absolute;
      bottom: 0;
      left: -400px;
      @media (max-width: 500px) {
        font-size: 18vw;
        left: -100px;
      }
    }
  }
  .indicator_scroll {
    flex-direction: column;
    justify-content: space-around;
    width: 89px;
    height: 107px;
    position: relative;
    span {
      width: 48px;
      height: 1px;
      border: 1px solid var(--black-color);
      transform: rotate(90deg);
      animation: scrollAnimation 2.5s infinite cubic-bezier(0, 1, 1, 1);
      position: absolute;
    }
  }
}
@keyframes scrollAnimation {
  0% {
    top: -28px;
    opacity: 0;
  }
  100% {
    top: -4px;
    opacity: 1;
  }
}
</style>
