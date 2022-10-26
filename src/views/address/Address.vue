<template>
  <div class="wrapper">
    <div class="title">
      我的地址
      <span class="title__create">
        <router-link to="/addressEdit">新建</router-link>
      </span>
    </div>
    <div
      class="empty"
      v-if="addressList.length === 0"
    >暂无地址数据</div>
    <div class="address">
      <div
        class="address__item"
        v-for="address in addressList"
        :key="address._id"
      >
        <p class="address__item__basic">
          {{ address.name }}
          <span class="address__item__phone">{{ address.phone }}</span>
        </p>
        <div class="address__item__address">
          {{ address.city }}{{ address.department }}{{ address.houseNumber }}
        </div>
        <div class="iconfont">&#xe779;</div>
      </div>
    </div>
  </div>
  <Docker :currentIndex="3" />
</template>

<script>
import { ref } from 'vue'
import { get } from '../../utils/request'
import Docker from '../../components/Docker'

// 地址列表逻辑
const useAddressListEffect = () => {
  const addressList = ref([])
  const getAddressList = async () => {
    const result = await get('/api/user/address')
    if (result?.errno === 0 && result?.data?.length) {
      addressList.value = result.data
    }
  }
  return { addressList, getAddressList }
}

export default {
  name: 'Address',
  components: { Docker },
  setup () {
    const { addressList, getAddressList } = useAddressListEffect()
    getAddressList()
    return { addressList }
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

    a {
      text-decoration: none;
      color: $content-fontColor;
    }
  }
}

.address {
  margin-top: .16rem .18rem 0 .18rem;

  &__item {
    position: relative;
    box-sizing: border-box;
    padding: .18rem .63rem .18rem .16rem;
    margin-bottom: .16rem;
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

.empty {
  @include empty;
}
</style>
