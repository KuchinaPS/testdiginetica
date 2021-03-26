<template>
  <div class="range">
    <h2 class="range__title">Цена, валюта</h2>
    <div class="range-value">
      <p class="range-value__container">от <span>{{ minPrice }}</span> до <span>{{ maxPrice }}</span></p>
    </div>

    <div class="range-price">
      <input @change="setRangeSliders" v-model.number="minPrice" type="range" min="0" max="1000" step="10">
      <input @change="setRangeSliders" v-model.number="maxPrice" type="range" min="0" max="1000" step="10">
    </div>
  </div>
</template>

<script>
export default {
  name: "RangePrice",
  data() {
    return {
      minPrice: 0,
      maxPrice: 1000,
    }
  },
  methods: {
    setRangeSliders() {
      if (this.minPrice > this.maxPrice) {
        let temp = this.maxPrice;
        this.maxPrice = this.minPrice;
        this.minPrice = temp;
      }
    }
  }
}
</script>

<style lang="scss" scoped>
input[type=range] {
  -webkit-appearance: none;
}

input[type=range]:focus {
  outline: none;
}
.range{
  padding-bottom: 36px;
  &__title{
    padding-bottom: 16px;
  }
}

.range-value {
  padding-bottom: 32px;
  &__container {
    font-size: 12px;
    line-height: 14px;
    color: rgba(0,0,0,0.5);

    & > span {
      border: 1px solid #DEDEDE;
      border-radius: 3px;
      font-family: Arial;
      font-size: 14px;
      line-height: 16px;
      color: #000000;
      padding: 12px 64px 12px 12px;
    }
  }
}

.range-price {
  align-items: center;
  position: relative;
}

input[type=range]::-webkit-slider-runnable-track {
  width: 500px;
  height: 4px;
  cursor: pointer;
  animate: 0.2s;
  background: #000000;
  border-radius: 4px;

}

.range-price svg,
.range-price input[type=range] {
  position: absolute;
  left: 0;
  bottom: 0;
  width: 100%;
}

input[type=range]::-webkit-slider-thumb {
  box-shadow: 1px 1px 1px #000000, 0px 0px 1px #0d0d0d;
  border: 2px solid #000000;
  height: 14px;
  width: 14px;
  border-radius: 50%;
  background: #ffffff;
  cursor: pointer;
  -webkit-appearance: none;
  margin-top: -4px;
  position: relative;
  z-index: 3;
}

</style>