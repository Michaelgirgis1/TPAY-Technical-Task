<template>
  <div class="game-card">
    <div class="game-card__img">
      <img src="../assets/images/game-four.jpeg" alt="" />
    </div>
    <h3 class="game-card__title">{{ title }}</h3>
    <button class="generic__btn">more info</button>
    <div class="game-card__rate">
      <div id="star-five"></div>
      <span class="game-card__rate__num">4.9</span>
    </div>
  </div>
</template>

<script>
export default {
  props: ["title", "description"],
};
</script>

<style lang="scss">
.game-card {
  position: relative;
  .game-card__img {
    position: relative;
    &::before {
      display: block;
      content: "";
      width: 100%;
      padding-top: 100%;
    }
    img {
      position: absolute;
      top: 0;
      right: 0;
      bottom: 0;
      left: 0;
      display: block;
      width: 100%;
    }
  }
  .game-card__title {
    line-height: 22px;
    height: 44px;
    overflow: hidden;
    font-size: calc(20px + ((24 - 20) * (100vw - 1366px) / (1920 - 1366)));
  }
  .game-card__rate {
    position: absolute;
    top: 10px;
    left: 10px;
    display: inline-flex;
    background: white;
    padding: 3px 10px;
    border-radius: 25px;
    #star-five {
      position: relative;
      display: inline-block;
      width: 0;
      height: 0;
      margin-left: 0;
      margin-right: 10px;
      margin-bottom: 0;
      border-right: 4.6px solid transparent;
      border-bottom: 13.4px solid #572589;
      border-left: 4.6px solid transparent;
      font-size: 24px;

      &:before,
      &:after {
        content: "";
        display: block;
        width: 0;
        height: 0;
        position: absolute;
        top: 7.2px;
        left: -10.5px;
        border-right: 10px solid transparent;
        border-bottom: 6.4px solid #572589;
        border-left: 11px solid transparent;
        transform: rotate(-35deg);
      }

      &:after {
        transform: rotate(35deg);
      }
    }
  }
}
@media (max-width: 1366px) {
  .game-card {
    .game-card__title {
      font-size: calc(16px + ((20 - 16) * (100vw - 320px) / (1366 - 320)));
    }
  }
}
</style>