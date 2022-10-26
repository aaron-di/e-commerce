<template>
  <div class="wrapper">
    <div class="title">
      新建地址
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

</style>
