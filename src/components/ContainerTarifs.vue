<template>
  <div class="container--price flex">
    <h2 class="container--title">TARIFS</h2>
    <div class="cards flex">
      <div class="card flex">
        <h3>Standard</h3>
        <h2>600€</h2>
        <ul class="card--list">
          <li>+ Responsive site</li>
          <li>+ Graphic charter from a pre-defined model</li>
          <li>+ Selection of a color palette</li>
        </ul>
        <a href="mailto: melvin.debot@hetic.net" class="flex"
          >Ask for an estimate</a
        >
      </div>
      <div class="card flex">
        <h3>Premium</h3>
        <h2>800€</h2>
        <ul class="card--list">
          <li>+ Responsive site</li>
          <li>+ Creation of personalized graphic charter</li>
          <li>+ Sharing links on social networks</li>
          <li>+ Optimization of referencing and performance</li>
          <li>
            + Addition of several functionalities according to your request
          </li>
        </ul>
        <a href="mailto: melvin.debot@hetic.net" class="flex"
          >Ask for an estimate</a
        >
      </div>
      <div class="card flex">
        <h3>Maintenance</h3>
        <h2>50€<span>/HOUR</span></h2>
        <ul class="card--list">
          <li>+ Website updates & plugins</li>
          <li>+ Small graphic or content modifications</li>
          <li>+ Performance optimization</li>
        </ul>
        <a href="mailto: melvin.debot@hetic.net" class="flex">contact me</a>
      </div>
    </div>
  </div>
</template>

<script>
import gsap, { Power1 } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";
gsap.registerPlugin(ScrollTrigger);
export default {
  name: "Tarifs",
  methods: {
    animationCard() {
      gsap
        .timeline({
          scrollTrigger: {
            trigger: ".container--price",
            start: "top center",
            end: "30% center",
            scrub: true,
          },
        })
        .fromTo(
          ".cards",
          1,
          {
            opacity: 0,
          },
          {
            opacity: 1,
            ease: Power1.easeInOut,
          }
        );
    },
  },
  mounted() {
    this.animationCard();
  },
};
</script>

<style lang="scss" scoped>
.container--price {
  width: 100%;
  height: 90vh;
  position: relative;
  overflow-x: hidden;
  @media (max-width: 500px) {
    height: 270vh;
  }
  .container--title {
    position: absolute;
    font-size: 10vw;
    right: -19%;
    top: 34%;
    font-weight: 900;
    transform: rotate(-90deg);
    opacity: 0.4;
    @media (max-width: 500px) {
      letter-spacing: 5px;
      right: -22%;
    }
  }
  .cards {
    width: 89%;
    height: 78vh;
    justify-content: space-around;
    position: relative;
    @media (max-width: 500px) {
      flex-direction: column;
      height: 266vh;
    }
    .card {
      flex-direction: column;
      justify-content: space-around;
      width: 29%;
      height: 504px;
      background: var(--light-color);
      border-radius: 10px;
      padding: 10px 0px;
      @media (max-width: 500px) {
        height: 450px;
        width: 100%;
      }
      &:nth-child(2) {
        @media (max-width: 500px) {
          .card--list {
            height: 60%;
          }
        }
      }
      &:nth-child(3) {
        background: var(--green-color);
        color: var(--white-color);
        h2 {
          span {
            font-size: 15px;
            font-weight: 300;
          }
        }
        a {
          background: white;
          color: var(--green-color);
        }
      }
      h3 {
        font-weight: 500;
        font-size: 2.5vw;
        @media (max-width: 500px) {
          font-size: 6.5vw;
        }
      }
      h2 {
        font-size: 3.6vw;
        @media (max-width: 500px) {
          font-size: 12.5vw;
        }
        span {
          border: none;
        }
      }
      .card--list {
        width: 90%;
        height: 50%;
        text-align: justify;
        list-style: none;
        li {
          margin-top: 10px;
          text-align: start;
        }
      }
      a {
        width: 223px;
        height: 53px;
        text-decoration: none;
        background: var(--green-color);
        color: var(--white-color);
        border: none;
        font-size: 18px;
      }
    }
  }
}
</style>
