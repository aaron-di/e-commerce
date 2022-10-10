<template>
  <div class="order">
    <div class="order__price">实付金额 <b>¥{{ calculations.price }}</b></div>
    <div class="order__btn" @click="() => handleSubmitClick(true)">提交订单</div>
  </div>
  <div class="mask" v-show="showConfirm" @click="() => handleSubmitClick(false)">
    <div class="mask__content" @click.stop>
      <h3 class="mask__content__title">确认要离开收银台？</h3>
      <p class="mask__content__desc">请尽快完成支付，否则订单将被取消</p>
      <div class="mask__content__btns">
        <div class="mask__content__btn mask__content__btn--first" @click="() => handleConfirmOrder(true)">取消订单</div>
        <div class="mask__content__btn mask__content__btn--last" @click="() => handleConfirmOrder(false)">确认支付</div>
      </div>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue'
import { useRoute, useRouter } from 'vue-router'
import { post } from '../../utils/request'
import { useCommonCartEffect } from '../../effects/cartEffects'
import store from '../../store'
export default {
  name: 'OrderConfirmation',
  setup () {
    const router = useRouter()
    const route = useRoute()
    const shopId = parseInt(route.params.id, 10)

    const showConfirm = ref(false)
    const { calculations, shopName, productList } = useCommonCartEffect(shopId)
    const handleSubmitClick = (status) => {
      showConfirm.value = status
    }

    const handleConfirmOrder = async (isCanceled) => {
      const products = []
      for (let i in productList.value) {
        const product = productList.value[i]
        products.push({ id: parseInt(product._id, 10), num: product.count })
      }

      try {
        const result = await post('/api/order', {
          addressId: 1,
          shopId,
          shopName: shopName.value,
          isCanceled,
          products
        })
        console.log(result)
        if (result?.errno === 0) {
          alert('下单完成，返回首页')
          store.commit('clearCartData', shopId)
          router.push({ name: 'Home' })
        }
      } catch (e) {
        alert('请求失败')
      }
    }

    return { showConfirm, handleSubmitClick, calculations, handleConfirmOrder }
  }
}
</script>

<style lang="scss" scoped>
@import '../../style/variables.scss';

.order {
  position: absolute;
  left: 0;
  right: 0;
  bottom: 0;
  display: flex;
  height: .49rem;
  line-height: .49rem;
  background: $bgColor;

  &__price {
    flex: 1;
    text-indent: .24rem;
    font-size: .14rem;
    color: $content-fontColor;
  }

  &__btn {
    width: .98rem;
    background: #4FB0F9;
    color: $bgColor;
    text-align: center;
    font-size: .14rem;
  }
}

.mask {
  z-index: 1;
  position: absolute;
  left: 0;
  right: 0;
  bottom: 0;
  top: 0;
  background: rgba(0, 0, 0, 0.5);

  &__content {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    width: 3rem;
    height: 1.56rem;
    background: #FFF;
    text-align: center;
    border-radius: .04rem;

    &__title {
      margin: .24rem 0 0 0;
      line-height: .26rem;
      font-size: .18rem;
      color: #333;
    }

    &__desc {
      margin: .08rem 0 0 0;
      font-size: .14rem;
      color: #666666;
    }

    &__btns {
      display: flex;
      margin: .24rem .58rem;
    }

    &__btn {
      flex: 1;
      width: .8rem;
      line-height: .32rem;
      border-radius: .16rem;
      font-size: .14rem;

      &--first {
        margin-right: .12rem;
        border: 1px solid #4FB0F9;
        color: #4FB0F9;
      }

      &--last {
        margin-left: .12rem;
        background: #4FB0F9;
        color: #FFF;
      }
    }
  }
}
</style>