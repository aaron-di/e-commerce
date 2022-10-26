<template>
  <div class="wrapper">
    <StaticPart />
    <NearBy />
  </div>
  <Docker :currentIndex="0" />
</template>

<script>
import StaticPart from './StaticPart.vue'
import NearBy from './Nearby.vue'
import Docker from '../../components/Docker.vue'
export default {
  name: 'Home',
  components: { StaticPart, NearBy, Docker }
}
</script>

<style lang="scss" scoped>
@import '../../style/mixins.scss';

.wrapper {
  overflow-y: auto;
  @include fix-content;
  padding: 0 .18rem .1rem .18rem;
}

</style>
