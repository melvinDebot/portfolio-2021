<template>
  <div class="home border--display" ref="scrollContainerPage">
    <div class="cursor-circle"></div>
    <ul class="list">
      <li>
        <a class="listTest" href="#home"> - Intro<span>01</span></a>
      </li>
      <li>
        <a class="listTest" href="#home"> - Projects <span>02</span></a>
      </li>
      <li>
        <a class="listTest" href="#home"> - About <span>03</span></a>
      </li>
      <li>
        <a class="listTest" href="#home"> - Price <span>04</span></a>
      </li>
      <li>
        <a class="listTest" href="#home"> - Contact <span>05</span></a>
      </li>
    </ul>
    <Header class="test-section" />
    <Container class="test-section" />
    <About class="test-section" />
    <ContainerTarifs class="test-section" />
    <Contact class="test-section" />
  </div>
</template>

<script>
// @ is an alias to /src
import Header from "@/components/Header.vue";
import Container from "@/components/Container.vue";
import ContainerTarifs from "@/components/ContainerTarifs.vue";
import Contact from "@/components/Contact.vue";
import About from "@/components/About.vue";

export default {
  name: "Home",
  components: {
    Header,
    Container,
    ContainerTarifs,
    Contact,
    About,
  },
  data() {
    return {
      mouseX: 0,
      mouseY: 0,
      xp: 0,
      yp: 0,
    };
  },
  methods: {},
  mounted() {
    // CONTAINER MOUSEMOVE CURSOR FOLLOW
    let circle = document.querySelector(".cursor-circle");
    this.$refs.scrollContainerPage.addEventListener("mousemove", (e) => {
      this.mouseX = e.pageX - 30;
      this.mouseY = e.pageY - 30;
      this.xp += (this.mouseX - this.xp) / 6;
      this.yp += (this.mouseY - this.yp) / 6;
      setInterval(() => {
        circle.style.left = this.xp + "px";
        circle.style.top = this.yp + "px";
      }, 20);
    });
    // SECTION DETECT SCROLL
    let menuSection = document.querySelectorAll(".listTest");
    let mainSection = document.querySelectorAll(".test-section");

    window.addEventListener("scroll", () => {
      mainSection.forEach((v, i) => {
        let rect = v.getBoundingClientRect().y;
        if (rect < window.innerHeight - 700) {
          console.log("window heigh :", window.innerHeight - 200);
          menuSection.forEach((v) => v.classList.remove("active"));
          menuSection[i].classList.add("active");
        }
      });
    });
  },
};
</script>

<style lang="scss" scoped>
.home {
  width: 100%;
  height: auto;
}
.cursor-circle {
  position: absolute;
  border: solid 1px var(--green-color);
  width: 60px;
  height: 60px;
  border-radius: 50%;
  animation: dipslayCursor 1s ease-in-out forwards;

  @media (max-width: 500px) {
    display: none;
  }
  @keyframes dipslayCursor {
    0% {
      opacity: 0;
    }
    100% {
      opacity: 1;
    }
  }
}
.list {
  position: fixed;
  width: 130px;
  height: 150px;
  right: 0;
  top: 10px;
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  align-content: flex-end;
  li {
    position: relative;
    a {
      text-decoration: none;
      color: var(--white-color);
      font-size: 18px;
      span {
        font-size: 14px;
        font-weight: 400;
        color: var(--white-color);
        margin-left: 10px;
      }
      &::before {
        width: 7px;
        height: 3px;
        background: var(--green-color);
        position: absolute;
        top: 0;
        left: 0;
      }
    }
  }
  @media (max-width: 500px) {
    display: none;
  }
}
.active {
  color: var(--black-color) !important;
  font-weight: 600;
  font-size: 20px;
  span {
    color: var(--green-color) !important;
  }
}
</style>
