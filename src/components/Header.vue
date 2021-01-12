<template>
  <div class="header display">
    <div class="subtitle flex">
      <h3>MELVIN DEBOT</h3>
    </div>
    <div class="title display">
      <h2 class="one">CREATIVE</h2>
      <h2 class="two">DEVELOPER</h2>
    </div>
    <div class="indicator_scroll flex">
      <span></span>
      scroll
    </div>
  </div>
</template>

<script>
export default {

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
  .title{
    width: 100%;
    height: 80%;
    position: relative;
    padding: 20px 0px;
    @media (max-width: 500px) {
      height: 30%;
    }
    h2{
      font-size: 15vw;
      font-weight: 900;
    }
    .one{
      position: absolute;
      top: 0;
      right: -200px;
      @media (max-width: 500px) {
        font-size: 16.5vw;
        right: -100px;
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
    }
  }
}
</style>