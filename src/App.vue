<template>
  <div id="app">
    <div class="header">
      <div class="header__container container">
        <div class="header__content">
          Шапка сайта
        </div>
      </div>
    </div>
    <div class="main-page">
      <div class="container">
        <Search></Search>
        <CarouselCategory></CarouselCategory>
        <div class="main-page__wrap">
          <div class="aside">
            <allCategory></allCategory>
            <div class="filters">
              <RangePrice></RangePrice>
              <div class="brand">
                <h2>Бренды</h2>
                <button @click="clearCheck" class="brand__clear">Очистить</button>
                <label for="product1">
                  <input v-model="check1" type="checkbox" id="product1">
                  Бренд (ххх)
                </label>
                <label for="product2">
                  <input v-model="check2" type="checkbox" id="product2">
                  Бренд (х)
                </label>
                <label for="product3">
                  <input v-model="check3" type="checkbox" id="product3">
                  Бренд (х ххх)
                </label>
              </div>
            </div>
          </div>
          <div class="main-cards">
            <div class="sort wrapper">
              <div class="sort__link">
                <span>Cортировать по:</span>
                <a href="#" class="active">пополуярности</a>
                <a href="#">сначала дешевые</a>
                <a href="#">сначала дорогие</a>
              </div>
              <div class="sort__page">
                <span>показывать по</span>
                <select name="page">
                  <option value="12">12</option>
                  <option value="24" selected>24</option>
                </select>
              </div>
            </div>
            <div class="tags">
              <ul class="tags__list">
                <li v-for="i in 4" :key="i" class="tags__item">Уточнение</li>
              </ul>
            </div>
            <div class="cards">
              <ul class="cards__list">
                <li v-for="i in 9" :key="i" class="cards__item card">
                  <div class="card__img"></div>
                  <div class="card__title">Наименование товара, которое не более 2 строк
                  </div>
                  <div class="wrapper">
                    <div class="card__price">ХХ ХХХ , $</div>
                    <div class="card__old-price">ХХ ХХХ , $</div>
                  </div>
                  <a class="btn card__button">Кнопка</a>
                </li>
              </ul>
              <div class="pagination"></div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Search from "@/components/Search";
import CarouselCategory from "@/components/CarouselCategory";
import allCategory from "@/components/allCategory";
import RangePrice from "@/components/RangePrice";

export default {
  name: 'App',
  components: {
    Search,
    CarouselCategory,
    allCategory,
    RangePrice
  },
  data() {
    return {
      check1: false,
      check2: false,
      check3: false,
    }
  },
  methods: {
    clearCheck() {
      this.check1 = false;
      this.check2 = false;
      this.check3 = false;
    }
  }
}
</script>

<style lang="scss">
@import './style/general.module.scss';
@import './style/container.module.scss';
@import "src/style/btn.module";

.main-page {
  padding-bottom: 42px;
  &__wrap {
    display: grid;
    grid-template-columns: minmax(200px, 1fr);
    gap: 40px;
    padding-top: 40px;
    @media screen and (min-width: 710px) {
      grid-template-columns: minmax(320px, 0.7fr) minmax(320px, 2fr);
    }
  }
}

.header {
  background-color: #000000;
  margin-bottom: 32px;

  &__container {
    color: #ffffff;
    display: flex;
    justify-content: right;
    align-items: center;
    min-height: 100px;
  }
}

.cards {

  &__list {
    display: grid;
    grid-template-rows: 1fr 1fr 1fr;
    grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
    grid-gap: 2vw;
  }
}

.card {
  max-width: 260px;
  cursor: pointer;
  transition: 500ms;
  &:hover{
    transform: scale(1.03);
  }

  &__img {
    max-width: 260px;
    height: 260px;
    background: #C4C4C4;
    border-radius: 3px;
  }

  &__title {
    font-family: Arial;
    font-weight: normal;
    font-size: 14px;
    line-height: 130%;
    letter-spacing: 0.01em;
    padding-bottom: 8px;
  }

  &__price {
    font-weight: bold;
    font-size: 16px;
    line-height: 16px;
    margin-right: 16px;
    padding-bottom: 16px;
  }

  &__old-price {
    font-size: 14px;
    line-height: 16px;
    text-decoration-line: line-through;
    color: #A9A9A9;
  }

  &__button {
    max-width: 260px;
    text-align: center;
    padding: 12px 0;
    display: block;
    cursor: pointer;
    transition: 500ms;

    &:hover,
    &:focus,
    &:active {
      background-color: #F8D073;
    }
  }
}

.wrapper {
  display: flex;
}

.sort {
  justify-content: space-between;
  padding-bottom: 24px;
  align-items: center;
  flex-wrap: wrap;

  &__link {
    & > span {
      margin-right: 8px;
    }

    & > a {
      color: #5375B7;
      font-size: inherit;
      text-decoration: none;
      margin-right: 16px;
      transition: 500ms;

      &:hover,
      &:focus,
      &:active {
        color: #000000;
      }
    }

    & > a.active {
      color: #000000;
      border-bottom: 1px solid #F1BD45;
    }
  }
}

.tags {
  padding-bottom: 20px;

  &__list {
    display: flex;
    flex-wrap: wrap;
  }

  &__item {
    background-color: #FFF3D8;
    border-radius: 3px;
    padding: 8px 16px;
    margin-right: 12px;
    margin-bottom: 4px;
    cursor: pointer;
    transition: 500ms;

    &:hover,
    &:focus,
    &:active {
      background-color: #F1BD45;
    }
  }
}

.brand {
  & > h2 {
    display: inline-block;
    margin-right: 20%;
    padding-bottom: 12px;
  }

  & > label {
    display: block;
    padding-bottom: 16px;
    cursor: pointer;
  }

  &__clear {
    display: inline-block;
    background-color: transparent;
    border: none;
    color: #333333;
    opacity: 0.5;
    text-decoration: underline;
    cursor: pointer;
    outline: none;
  }
}
</style>
