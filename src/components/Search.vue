<template>
  <div class="search">
    <div>
      <label class="search__label" for="searchUser">
        <input v-model="searchString" type="text" class="search__inp" placeholder="Запрос пользователя"
               id="searchUser"></label>
      <a href="#" class="btn btn--search search__button">Найти</a>
      <button class="btn btn--close search__close" @click="clearInput">Закрыть</button>
    </div>
    <div class="search__result">
      <h1 class="search__title">Результаты по запросу</h1>
      <p class="search__subtitle" :class="{ 'search__subtitle--active': this.searchString}">Показаны результаты для
        “{{ this.searchString }}”. Вы искали “{{ this.searchString }}”.</p>
    </div>

  </div>

</template>

<script>
export default {
  name: "Search",
  data() {
    return {
      searchString: "",
    }
  },
  methods: {
    clearInput() {
      this.searchString = "";
    }
  }
}
</script>


<style lang="scss" scoped>
@import "src/style/btn.module";

.search {
  & > div {
    padding-top: 32px;
    display: flex;
    align-items: center;
  }

  &__label {
    flex: 1 1 77%;
    position: relative;

    &:before {
      content: "";
      position: absolute;
      top: 12px;
      left: 24px;
      width: 17px;
      height: 17px;
      background-image: url("../assets/search.svg");
    }
  }

  &__inp {
    width: 100%;
    padding: 12px 0 12px 56px;
    background: #FFFFFF;
    border: 1px solid #C7C7C7;
    border-radius: 5px 0px 0px 5px;
    line-height: 1.14;
    font-size: 14px;
    outline: none;
    transition: 500ms;

    &:after {
      content: "";
      position: absolute;
      width: 10px;
      height: 10px;
      background-color: red;
      top: 0;
      left: 0;
      z-index: 100;
    }
    &:hover,
    &:focus,
    &:active{
      outline: none;
      border: 1px solid #F1BD45;
    }
  }

  &__result {
    flex-direction: column;
    @media screen and (min-width: 710px) {
      flex-direction: row;
    }
  }

  &__title {
    font-family: Arial;
    font-size: 28px;
    margin-right: 20px;
  }

  &__subtitle {
    font-family: inherit;
    font-size: 14px;
    line-height: 19px;
    color: #8B8B8B;
    display: none;

    &--active {
      display: inline;
    }
  }

  &__button {
    flex: 0 0 5%;
    color: inherit;
    text-decoration: none;
    padding: 12px 4%;
    margin-right: 12px;
    transition: 500ms;
    &:hover,
    &:focus,
    &:active{
      background-color: #9D7416;
    }
  }

  &__close {
    flex: 0 0 5%;
    padding: 12px 24px;
    display: none;
    transition: 500ms;
    cursor: pointer;
    &:hover,
    &:focus,
    &:active{
      background-color: #9D7416;
    }

    @media screen and (min-width: 710px) {
      display: block;
    }
  }
}


</style>