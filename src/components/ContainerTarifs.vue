<template>
  <div class="container--price flex display">
    <h2 class="container--title">TARIFS</h2>
    <div class="cards flex">
      <div class="card flex">
        <h3>Standard</h3>
        <h2>999e</h2>
        <ul class="card--list display">
          <li>+Site responsive</li>
          <li>+Charte graphique à partir d'une maquette pré-définie</li>
          <li>+Sélection d'une palette de couleur</li>
          <li>+Site responsive</li>
        </ul>
        <button>Demandez un devis</button>
      </div>
      <div class="card flex">
        <h3>Standard</h3>
        <h2>999e</h2>
        <ul class="card--list display">
          <li>+ Site responsive</li>
          <li>+ Site responsive</li>
          <li>+ Site responsive</li>
          <li>+ Site responsive</li>
        </ul>
        <button>Demandez un devis</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name:"Tarifs"
}
</script>

<style lang="scss" scoped>
.container--price{
  width: 100%;
  height: 80vh;
  position: relative;
  overflow-x: hidden;
  .container--title{
    position: absolute;
    font-size: 10vw;
    right: -19%;
    top: 50%;
    font-weight: 900;
    transform: rotate(-90deg);
    opacity: 0.4;
  }
  .cards{
    width: 80%;
    height: 662px;
    justify-content: space-around;
    @media (max-width: 500px) {
      flex-direction: column;
      height: 150vh;
    }
    .card{
      flex-direction: column;
      justify-content: space-around;
      width: 35%;
      height: 443px;
      background: #E4E4E4;
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