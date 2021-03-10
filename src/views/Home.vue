<template>
  <div class="home border--display" ref="scrollContainerPage">
    <div class="cursor-circle"></div>

    <Header />
    <Container />
    <About />
    <ContainerTarifs />
    <Contact />
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
  methods: {
    scrollContainerPage(e) {
      this.mouseX = e.pageX - 30;
      this.mouseY = e.pageY - 30;
    },
  },
  mounted() {
    let circle = document.querySelector(".cursor-circle");
    this.$refs.scrollContainerPage.addEventListener("mousemove", (e) => {
      this.mouseX = e.pageX - 30;
      this.mouseY = e.pageY - 30;
      this.xp += (this.mouseX - this.xp) / 6;
      this.yp += (this.mouseY - this.yp) / 6;

      setInterval(() => {}, 40);
      setInterval(() => {
        circle.style.left = this.xp + "px";
        circle.style.top = this.yp + "px";
      }, 20);
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
  animation: dipslayCursor  1s ease-in-out forwards;

  @media (max-width: 500px) {
    display: none;
  }
  @keyframes dipslayCursor {
    0%{
      opacity: 0;
    }
    100%{
      opacity: 1;
    }
  }
}
</style>
