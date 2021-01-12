<template>
  <div class="container--price flex">
    <h2 class="container--title">TARIFS</h2>
    <div class="cards flex">
      <div class="card flex">
        <h3>Standard</h3>
        <h2>600e</h2>
        <ul class="card--list">
          <li>+ Site responsive</li>
          <li>+ Charte graphique à partir d'une maquette pré-définie</li>
          <li>+ Sélection d'une palette de couleur</li>
          <li>+ Site responsive</li>
        </ul>
        <button>Demandez un devis</button>
      </div>
      <div class="card flex">
        <h3>Standard</h3>
        <h2>800e</h2>
        <ul class="card--list">
          <li>+ Site responsive</li>
          <li>+ Création charte graphique personnalisée</li>
          <li>+ Liens de partage sur les réseaux sociaux</li>
          <li>+ Optimisation du référencement et des performances</li>
          <li>+ Ajout de plusieurs fonctionnalités selon votre demande</li>
        </ul>
        <button>Demandez un devis</button>
      </div>
    </div>
  </div>
</template>

<script>
import gsap, {Power1} from 'gsap'
import { ScrollTrigger } from "gsap/ScrollTrigger";
gsap.registerPlugin(ScrollTrigger);
export default {
  name:"Tarifs",
  methods : {
    animationCard(){
      gsap.timeline({
        scrollTrigger : {
          trigger: ".container--price",
          start: "top center",
          end: "30% center",
          markers: true,
          scrub: true,
        }
      })
      .fromTo('.cards',1, 
        {
          opacity: 0
        },
        {
          opacity: 1,
          ease: Power1.easeInOut
        }
      )
    }
  },
  mounted(){
    this.animationCard()
  }
}
</script>

<style lang="scss" scoped>
.container--price{
  width: 100%;
  height: 80vh;
  position: relative;
  overflow-x: hidden;
  @media (max-width: 500px) {
    height: 160vh;
  }
  .container--title{
    position: absolute;
    font-size: 10vw;
    right: -19%;
    top: 34%;
    font-weight: 900;
    transform: rotate(-90deg);
    opacity: 0.4;
  }
  .cards{
    width: 80%;
    height: 662px;
    justify-content: space-around;
    position: relative;
    @media (max-width: 500px) {
      flex-direction: column;
      height: 150vh;
    }
    .card{
      flex-direction: column;
      justify-content: space-around;
      width: 35%;
      height: 478px;
      background: #F4F4F4;
      @media (max-width: 500px) {
        width: 100%;
      }
      h3{
        font-weight: 500;
        font-size: 2.5vw;
        @media (max-width: 500px) {
          font-size: 6.5vw;
        }
      }
      .card--list{
        width: 90%;
        height: 50%;
        text-align: justify;
        list-style: none;
        li{
          margin-top: 10px;
          text-align: start;
        }
      }
      button{
        width: 223px;
        height: 53px;
        background: #16BF15;
        color: white;
        border: none;
      }
    }
  }
}
</style>