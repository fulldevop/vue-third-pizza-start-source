<template>

        <div class="ingredients__filling">
          <p>Начинка:</p>

          <ul class="ingredients__list">
            <li
              v-for="ingredient in ingredientItems"
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
                  @click="modelValue[ingredient.value]--"
                  :disabled="modelValue[ingredient.value] === 0"
                >
                  <span class="visually-hidden">Меньше</span>
                </button>
                <input
                  type="text"
                  name="counter"
                  class="counter__input"
                  v-model="modelValue[ingredient.value]"
                />
                <button
                  type="button"
                  class="counter__button counter__button--plus"
                  @click="modelValue[ingredient.value]++"
                  :disabled="modelValue[ingredient.value] === 3"
                >
                  <span class="visually-hidden">Больше</span>
                </button>
              </div>
            </li>
          </ul>
        </div>
</template>

<script setup>
import { getImage } from "@/common/helper";

const props = defineProps({
  ingredientItems: {
    type: Array,
    default: () => [],
  },
});

const modelValue = defineModel();

const incrementValue = (ingredient) => {
  const oldCount = getValue(ingredient);
  const newCount = oldCount + 1;
  // setValue(ingredientId, newCount);
  emit("update", ingredient, newCount);
};

function getValue(ingredient) {
  return props.values[ingredient];
}

const emit = defineEmits(["update"]);
</script>

<style scoped lang="scss">
@import "@/assets/scss/ds-system/ds.scss";
@import "@/assets/scss/mixins/mixins.scss";

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
