<template>
  <div class="item">
    <div class="circle-group-1">
      <div class="circle"></div>
      <div class="circle"></div>
      <div class="circle"></div>
      <div class="circle"></div>
    </div>
    <div class="circle-group-2">
      <div class="circle"></div>
      <div class="circle"></div>
      <div class="circle"></div>
      <div class="circle"></div>
    </div>
  </div>
</template>

<style lang="stylus" scoped>
.item
  position relative
  width 350px
  height 350px
  animation spin 6s infinite cubic-bezier(0.55, 0.09, 0.68, 0.53)
  animation-delay 1s

  .circle-group-1, .circle-group-2
    position absolute
    top 0
    left 0
    width 100%
    height 100%

    .circle
      position absolute
      border 5px solid #aaa
      border-radius 50%

  .circle-group-1
    .circle
      width 40px
      height 40px
      animation circle-1-light 1s linear infinite

      &:nth-child(1)
        top 0
        left 50%
        transform translateX(-50%)

      &:nth-child(2)
        left 0
        top 50%
        transform translateY(-50%)
        animation-delay 0.25s

      &:nth-child(3)
        bottom 0
        left 50%
        transform translateX(-50%)
        animation-delay 0.5s

      &:nth-child(4)
        right 0
        top 50%
        transform translateY(-50%)
        animation-delay 0.75s

  .circle-group-2
    animation spin 6s infinite ease-in-out

    .circle
      width 15px
      height 15px
      border-width 2px
      animation circle-2-light 1s linear infinite

      &:nth-child(1)
        top 20%
        left 20%
        animation-delay 0.625s

      &:nth-child(2)
        bottom 20%
        left 20%
        animation-delay 0.125s

      &:nth-child(3)
        bottom 20%
        right 20%
        animation-delay 0.875s

      &:nth-child(4)
        top 20%
        right 20%
        animation-delay 0.375s

@keyframes circle-1-light
  0%
    background transparent

  25%
    background #fff
    box-shadow 0 0 20px #fff

  50%
    background transparent

  100%
    background transparent

@keyframes circle-2-light
  0%
    background transparent

  25%
    background #fff
    box-shadow 0 0 5px #fff

  50%
    background transparent

  100%
    background transparent

@keyframes spin
  0%
    transform rotate(0deg)

  8.3%
    transform rotate(-90deg)

  24.8%
    transform rotate(-90deg)

  32.1%
    transform rotate(-180deg)

  49.8%
    transform rotate(-180deg)

  58.1%
    transform rotate(-270deg)

  74.8%
    transform rotate(-270deg)

  83.1%
    transform rotate(-360deg)

  100%
    transform rotate(-360deg)
</style>
