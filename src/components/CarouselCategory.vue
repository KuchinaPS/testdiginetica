<template>
  <div class="carousel">
    <ul class="carousel__list">
      <li v-for="i in 5" :key="i" class="carousel__item">
        <a class="carousel__link" href="#">
          <div class="carousel__img"></div>
          <div class="carousel__wrap">
            <h3 class="carousel__title">Название категории</h3>
            <p class="carousel__count">134 товара</p>
          </div>
        </a>
      </li>
    </ul>


  </div>
</template>

<script>
export default {
  name: "CarouselCategory"
}
</script>

<style lang="scss" scoped>
.carousel {
padding-top: 32px;
  &__img {
    width: 60px;
    height: 60px;
    background-color: #C4C4C4;
    margin-right: 2px;
  }
  &__list{
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
    margin-bottom: 4px;
  }

  &__link{
    display: flex;
    margin-bottom: 4px;
    text-decoration: none;
    color: #000000;
    transition: 500ms;

    &:hover{
      transform: scale(1.1);
      text-decoration: underline;
    }

  }

  &__title{
    font-family: inherit;
    font-size: 14px;
    line-height: 19px;
  }
  &__count{
    font-family: inherit;
    font-size: 12px;
    line-height: 16px;
    color:#8B8B8B;
  }
}
</style>