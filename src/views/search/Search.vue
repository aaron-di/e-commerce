<template>
  <div class="wrapper">
    <div class="search">
      <span class="iconfont">&#xe752;</span>
      <input
        type="text"
        class="search__area"
        @change="handleSearchChange"
        placeholder="山姆会员商店优惠产品"
      >
      <div class="search__cancel" @click="handleCancelSearchClick">取消</div>
    </div>
    <div class="area" v-if="history.length">
      <h4 class="area__title">
        搜索历史
        <span
          class="area__title__clear"
          @click="handleClearHistoryClick"
        >清除搜索历史</span>
      </h4>
      <ul class="area__list">
        <li
          class="area__list__item"
          v-for="item in history"
          :key="item"
        >{{ item }}</li>
      </ul>
    </div>
    <div class="area">
      <h4 class="area__title">热门搜索</h4>
      <ul class="area__list">
        <li class="area__list__item">尖椒肉丝</li>
        <li class="area__list__item">鲜花</li>
        <li class="area__list__item">山姆会员商店</li>
        <li class="area__list__item">新鲜水果</li>
        <li class="area__list__item">生日鲜花</li>
      </ul>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue'
import { useRouter } from 'vue-router'

export default {
  name: 'Search',
  setup () {
    const router = useRouter()
    const history = ref(JSON.parse(localStorage.history || '[]'))
    // 当用户输入搜索内容后，执行的操作
    const handleSearchChange = (e) => {
      const searchValue = e.target.value
      if (!searchValue) return
      const hasValue = history.value.find(item => item === searchValue)
      if (!hasValue) {
        history.value.push(searchValue)
        localStorage.history = JSON.stringify(history.value)
      }
      router.push(`/searchList?keyword=${searchValue}`)
    }
    // 当清理历史记录时，执行的操作
    const handleClearHistoryClick = () => {
      history.value = []
      localStorage.history = JSON.stringify([])
    }
    // 当取消搜索时，执行的操作
    const handleCancelSearchClick = () => {
      router.back()
    }
    return {
      history,
      handleSearchChange,
      handleClearHistoryClick,
      handleCancelSearchClick
    }
  }
}
</script>

<style lang="scss" scoped>
.wrapper {
  margin: 0 .18rem;

  .search {
    position: relative;
    display: flex;
    line-height: .32rem;
    margin-top: .16rem;
    color: #666;

    .iconfont {
      position: absolute;
      left: .16rem;
      color: #B7B7B7;
    }

    &__area {
      flex: 1;
      padding: 0 .12rem 0 .44rem;
      background: #F5F5F5;
      border-radius: .16rem;
      border: none;
      outline: none;
      font-size: .14rem;
    }

    &__cancel {
      margin-left: .12rem;
      font-size: .16rem;
    }
  }

  .area {
    margin-top: .24rem;
    &__title {
      line-height: .22rem;
      margin: 0;
      font-size: .16rem;
      font-weight: normal;
      color: #333;

      &__clear {
        float: right;
        font-size: .14rem;
      }
    }

    &__list {
      margin: 0 0 0 -.1rem;
      padding: 0;
      list-style-type: none;

      &__item {
        line-height: .32rem;
        margin-left: .1rem;
        margin-top: .12rem;
        padding: 0 .1rem;
        font-size: .14rem;
        background: #F5F5F5;
        display: inline-block;
        border-radius: .02rem;
        color: #666;
      }
    }
  }
}
</style>
