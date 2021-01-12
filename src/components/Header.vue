<template>
  <div class="header">
    <div class="subtitle flex">
      <h3 ref="nameUser">MELVIN DEBOT</h3>
    </div>
    <div class="title">
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
import gsap, {Power3} from 'gsap'
export default {
  name: 'HEADER',
  data : function(){
    return {

    }
  },
  methods : {
    animationHeader(){
      gsap.fromTo(this.$refs.textOne, 1,{ x : "30%", opacity : 0, ease : Power3.easeInOut}, { x : '0%', opacity : 1, ease : Power3.easeOut})
      gsap.fromTo(this.$refs.textTwo, 1,{ x : "-30%", opacity : 0, ease : Power3.easeInOut}, { x : '0%', opacity : 1, ease : Power3.easeOut})
      gsap.fromTo(this.$refs.nameUser, 1 ,
        {
          y : -10,
          opacity : 0,
          ease : Power3.easeIn,
        },
        {
          y: 0,
          opacity : 1,
          ease : Power3.easeIn,
        }
      )
    }
  },
  created(){
    
  },
  mounted(){
    this.animationHeader()
  }
}
</script>

<style lang="scss" scoped>
@import url('/styles/header.scss');
.header{
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-direction: column;
  overflow-x: hidden;
  h3{
    opacity: 1;
  }
  .title{
    width: 100%;
    height: 50%;
    position: relative;
    padding: 20px 0px;
    @media (max-width: 500px) {
      height: 20%;
    }
    h2{
      font-size: 15vw;
      font-weight: 900;
    }
    .one{
      position: absolute;
      top: 0;
      // right: -200px;
      right: -200px;
      @media (max-width: 500px) {
        font-size: 16.5vw;
        right: -85px;
      }
    }
    .two{
      position: absolute;
      bottom: 0;
      left: -400px;
      @media (max-width: 500px) {
        font-size: 16.5vw;
        left: -100px;
      }
    }
  }
  .indicator_scroll{
    flex-direction: column;
    justify-content: space-around;
    width: 89px;
      height: 107px;
    span{
      width: 78px;
      height: 1px;
      border: 1px solid #000000;
      transform: rotate(90deg);
      animation: scrollAnimation 2s infinite cubic-bezier(0, 1, 1, 1);
    }
  }
}
@keyframes scrollAnimation {
  0% {
    width: 78;
  }
  100%{
    width: 0px;
  }
}
</style>