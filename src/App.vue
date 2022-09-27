<template>
  <div class="wrapper">
    <div class="position">
      <span class="iconfont position__icon">&#xe769;</span>
      五角场合生汇综合广场 - Apple Store
      <span class="iconfont position__notice">&#xe759;</span>
    </div>
  </div>
  <div class="docker">
    <div class="docker__item docker__item--active">
      <div class="iconfont">&#xe750;</div>
      <div class="docker__item__title">首页</div>
    </div>
    <div class="docker__item">
      <div class="iconfont">&#xe73e;</div>
      <div class="docker__item__title">购物车</div>
    </div>
    <div class="docker__item">
      <div class="iconfont">&#xe737;</div>
      <div class="docker__item__title">订单</div>
    </div>
    <div class="docker__item">
      <div class="iconfont">&#xe75e;</div>
      <div class="docker__item__title">我的</div>
    </div>
  </div>
</template>

<style lang="scss">
@import './style/variables.scss';
@import './style/mixins.scss';
.wrapper {
  position: absolute;
  left: 0;
  top: 0;
  bottom: .5rem;
  right: 0;
  padding: 0 .18rem;
}

.position {
  position: relative;
  padding: .16rem .24rem .16rem 0;
  line-height: .22rem;
  font-size: .16rem;
  @include ellipsis;
  color: $content-font-color;

  .position__icon {
    position: relative;
    top: .01rem;
    font-size: .2rem;
  }

  .position__notice {
    position: absolute;
    right: 0;
    top: .17rem;
    font-size: .2rem;
  }
}

.docker {
  display: flex;
  box-sizing: border-box;
  position: absolute;
  padding: 0 .18rem;
  left: 0;
  bottom: 0;
  width: 100%;
  height: .49rem;
  border-top: 1px solid #F1F1F1;
  color: $content-font-color;

  &__item {
    flex: 1;
    text-align: center;

    .iconfont {
      margin: .07rem 0 .02rem 0;
      font-size: .18rem;
    }

    &--active {
      color: #1FA4FC;
    }

    &__title {
      font-size: .2rem;
      transform: scale(.5, .5);
      transform-origin: center top;
    }
  }
}
</style>
