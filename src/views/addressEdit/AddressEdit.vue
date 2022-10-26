<template>
  <div class="wrapper">
    <div class="title">
      <div class="iconfont" @click="handleBackClick">
        &#xe779;
      </div>
      新建地址
      <span
        class="title__save"
        @click="handleSaveClick"
      >保存</span>
    </div>
    <div class="content">
      <div class="content__item">
        <span class="content__item__label">所在城市：</span>
        <input
          class="content__item__input"
          placeholder="请输入所在城市"
          v-model="city"
        />
      </div>
      <div class="content__item">
        <span class="content__item__label">小区/大厦/学校：</span>
        <input
          class="content__item__input"
          placeholder="请输入小区/大厦/学校"
          v-model="department"
        />
      </div>
      <div class="content__item">
        <span class="content__item__label">楼号-门牌号：</span>
        <input
          class="content__item__input"
          placeholder="请输入楼号-门牌号"
          v-model="houseNumber"
        />
      </div>
      <div class="content__item">
        <span class="content__item__label">收货人：</span>
        <input
          class="content__item__input"
          placeholder="请输入收货人"
          v-model="name"
        />
      </div>
      <div class="content__item">
        <span class="content__item__label">联系电话：</span>
        <input
          class="content__item__input"
          placeholder="请输入联系电话"
          v-model="phone"
        />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'AddressEdit',
  setup () {
    return { }
  }
}
</script>

<style lang="scss" scoped>
@import '../../style/variables.scss';
@import '../../style/mixins.scss';

.wrapper {
  overflow: scroll;
  position: absolute;
  left: 0;
  right: 0;
  top: 0;
  bottom: 0;
  background: $darkBgColor;
}

.title {
  position: relative;
  @include title;

  .iconfont {
    position: absolute;
    left: .1rem;
    width: .3rem;
    font-size: .24rem;
    color: $search-fontColor;
  }

  &__save {
    position: absolute;
    right: .18rem;
    font-size: .14rem;
    color: $content-fontColor;
  }
}

.content {
  margin-top: .12rem;
  padding: 0 .18rem;
  background: $bgColor;
  &__item {
    display: flex;
    overflow: hidden;
    height: .44rem;
    line-height: .44rem;
    border-bottom: .01rem solid $content-bgColor;
    font-size: .14rem;
    &__label {
      color: $content-fontColor;
    }
     &__input {
       flex: 1;
       border: none;
       outline: none;
     }
  }
}
</style>
