<template>
  <div class="wrapper">
    <StaticPart />
    <NearBy />
  </div>
  <Docker />
</template>

<script>
import StaticPart from './StaticPart.vue'
import NearBy from './Nearby.vue'
import Docker from './Docker.vue'
export default {
  name: 'Home',
  components: { StaticPart, NearBy, Docker }
}
</script>

<style lang="scss">
.wrapper {
  overflow-y: auto;
  position: absolute;
  left: 0;
  top: 0;
  bottom: .5rem;
  right: 0;
  padding: 0 .18rem .1rem .18rem;
}

</style>
