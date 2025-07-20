<template>
  <div class="content__ingredients">
    <div class="sheet">
      <h2 class="title title--small sheet__title">Выберите ингредиенты</h2>

      <div class="sheet__content ingredients">
        <SauceSelector />

        <div class="ingredients__filling">
          <p>Начинка:</p>

          <ul class="ingredients__list">
            <li
              v-for="ingredient in items"
              :key="ingredient.id"
              class="ingredients__item"
            >
              <div :class="`filling filling--${ingredient.value}`">
                <img
                  :src="getImage(ingredient.image)"
                  :alt="`${ingredient.name}`"
                />
                {{ ingredient.name }}
              </div>

              <div class="counter counter--orange ingredients__counter">
                <button
                  type="button"
                  class="counter__button counter__button--minus"
                  disabled
                >
                  <span class="visually-hidden">Меньше</span>
                </button>
                <input
                  type="text"
                  name="counter"
                  class="counter__input"
                  :value="getValue(ingredient.value)"
                />
                <button
                  type="button"
                  class="counter__button counter__button--plus"
                  @click="incrementValue(ingredient.value)"
                >
                  <span class="visually-hidden">Больше</span>
                </button>
              </div>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { getImage } from "@/common/helper";
import SauceSelector from "@/modules/constructor/SauceSelector.vue";

const props = defineProps({
  values: {
    type: Array,
    default: () => {},
  },
  items: {
    type: Array,
    default: () => [],
  },
});

const incrementValue = (ingredient) => {
  const oldCount = getValue(ingredient);
  const newCount = oldCount + 1;
  // setValue(ingredientId, newCount);
  emit("update", ingredient, newCount);
};

function getValue(ingredient) {
  return props.values[ingredient];
}

/*function setValue(id, count) {
  props.values.map((elem) => {
    if (elem.id === id) {
      return elem.count;
    }
  })
}*/

const emit = defineEmits(["update"]);
</script>

<style scoped lang="scss">
@import "@/assets/scss/ds-system/ds.scss";
@import "@/assets/scss/mixins/mixins.scss";

.content__ingredients {
  width: 527px;
  margin-top: 15px;
  margin-right: auto;
  margin-bottom: 15px;
}

.ingredients__sauce {
  display: flex;
  align-items: center;
  flex-wrap: wrap;

  width: 100%;
  margin-bottom: 14px;

  p {
    @include r-s16-h19;

    margin-top: 0;
    margin-right: 16px;
    margin-bottom: 10px;
  }
}

.ingredients__input {
  margin-right: 24px;
  margin-bottom: 10px;
}

.ingredients__filling {
  width: 100%;

  p {
    @include r-s16-h19;

    margin-top: 0;
    margin-bottom: 16px;
  }
}

.ingredients__list {
  @include clear-list;

  display: flex;
  align-items: flex-start;
  flex-wrap: wrap;
}

.ingredients__item {
  width: 100px;
  min-height: 40px;
  margin-right: 17px;
  margin-bottom: 35px;
}

.ingredients__counter {
  width: 54px;
  margin-top: 10px;
  margin-left: 36px;
}
</style>
