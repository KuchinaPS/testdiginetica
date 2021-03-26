<template>
  <div class="allCategory">
    <h2>Все категории</h2>
    <ul class="allCategory__list">
      <li v-for="i in 8" :key="i" class="allCategory__item"><a href="#">Категория в которой нашла что-то <span>(xxx)</span></a></li>
    </ul>
    <a class="allCategory__more" href="#">Еще 10 категорий..</a>
  </div>

</template>

<script>
export default {
  name: "allCategory"
}
</script>

<style lang="scss" scoped>
.allCategory{
  padding-bottom: 48px;
  &>h2{
    padding-bottom: 12px;
  }
  &__item{
    &>a{
      display: inline-block;
      color:#5375B7;
      padding-bottom: 8px;
      transition: 500ms;
      &>span{
        color: #8B8B8B;
      }
      &:hover,
      &:focus,
      &:active{
        color: #000000;
      }
    }
  }
  &__more{
    color:#5375B7;
  }
}

</style>