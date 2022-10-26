<template>
  <div class="wrapper">
    <div class="title">
      我的地址
      <span class="title__create">新建</span>
    </div>
    <div class="address">
      <div class="address__item">
        <p class="address__item__basic">
          小影
          <span class="address__item__phone">13688888888</span>
        </p>
        <div class="address__item__address">
          上海市翻斗花园1号楼101室
        </div>
        <div class="iconfont">&#xe779;</div>
      </div>
    </div>
  </div>
  <Docker :currentIndex="3" />
</template>

<script>
import Docker from '../../components/Docker'
export default {
  name: 'Address',
  components: { Docker },
  setup () {
    return {}
  }
}
</script>

<style lang="scss" scoped>
@import '../../style/variables.scss';
@import '../../style/mixins.scss';

.wrapper {
  overflow-y: auto;
  @include fix-content;
  background: $darkBgColor;
}

.title {
  position: relative;
  @include title;

  &__create {
    position: absolute;
    right: .18rem;
    font-size: .14rem;
  }
}

.address {
  margin-top: .16rem .18rem 0 .18rem;

  &__item {
    position: relative;
    box-sizing: border-box;
    padding: .18rem .63rem .18rem .16rem;
    margin-bottom: 1.6rem;
    background: $bgColor;
    border-radius: .04rem;

    &__basic {
      line-height: .2rem;
      margin: 0;
      font-size: .14rem;
      color: $light-fontColor;
    }

    &__phone {
      margin-left: .66rem;
    }

    &__address {
      line-height: .2rem;
      margin: .08rem 0 0 0;
      font-size: .14rem;
      color: $content-fontColor;
    }

    .iconfont {
      transform: rotate(180deg);
      position: absolute;
      right: .16rem;
      top: .44rem;
      color: $light-fontColor;
      font-size: .2rem;
    }
  }
}
</style>
