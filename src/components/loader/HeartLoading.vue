<template>
  <div class="rhombus2-container">
    <div class="rhombus2">
      <div class="circle21"></div>
      <div class="circle22"></div>
  </div>
  </div>  
  
</template>

<script>
export default {
    name: 'HeartLoading'

}
</script>

<style lang='scss' scoped>
$rhombus-size: 90px;
$circle-size: 40px;
.rhombus2-container{
  .rhombus2 {
    margin: 40px 0 0 60px;
    /*background: #fcfcfc;*/
    margin: auto;
    border-radius: 10px;
    height: $rhombus-size;
    width: $rhombus-size;
    margin-bottom: 10px;
    float: center;
    animation-delay: 0.9s;
    animation-duration: 0.8s;
    animation-name: pump;
    animation-iteration-count: infinite;
    animation-direction: alternate;
    animation-timing-function: cubic-bezier(.26,-0.53,.57,2.32);

    &:before {
      content: "";
      position: absolute;
      background: #EA4C89;
      height: $circle-size;
      width: $circle-size;
      z-index: 0;
      margin-top: 15px;
      margin-left: 15px;
      transform: rotate(45deg);
    }

  .circle21 {
    content: "";
    position: absolute;
    background: #EA4C89;
    height: $circle-size;
    width: $circle-size;
    z-index: 1;
    border-radius: 50%;
    /*animation-direction: alternate;*/
}

  .circle22 {
    content: "";
    position: absolute;
    background: #EA4C89;
    height: $circle-size;
    width: $circle-size;
    z-index: 1;
    margin-left: 30px;
    border-radius: 50%;
    /*animation-direction: alternate;*/
  }
}

@keyframes pump {
    0%{
        transform: scale(1);
    }
    100%{
        transform: scale(1.1);
    }
}

@keyframes change1 {
    0%,
    25% {
        margin-top: 0px;
        margin-left: 0px;
    }
    50%,
    75% {
        margin-top: 30px;
        margin-left: 30px;
    }
}

@keyframes change2 {
    25%,
    50% {
        margin-top: 30px;
        margin-left: 0px;
    }
    75%,
    100% {
        margin-top: 0px;
        margin-left: 30px;
    }
  }
}
</style>