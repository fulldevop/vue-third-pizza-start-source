<template>
  <app-drop>
    {{ modelValue.dough }}
    <div :class="`pizza pizza--foundation--${modelValue.dough}-tomato`">
      <div class="pizza__wrapper">
        <template v-for="(value, key, index) in modelValue.ingredients"
                  :key="index">
          <div v-if="value !== 0"
               :class="`pizza__filling pizza__filling--${key}`"></div>
        </template>
      </div>
    </div>
  </app-drop>
</template>

<script setup>
import AppDrop from "@/common/components/AppDrop.vue";

const modelValue = defineModel();
console.log(modelValue);

defineEmits(['drop'])
</script>

<style scoped lang="scss">

.pizza {
  position: relative;

  display: block;

  box-sizing: border-box;
  width: 100%;

  background-repeat: no-repeat;
  background-position: center;
  background-size: 100%;

  &--foundation--large-creamy {
    background-image: url("@/assets/img/foundation/large-creamy.svg");
  }

  &--foundation--large-tomato {
    background-image: url("@/assets/img/foundation/large-tomato.svg");
  }

  &--foundation--light-creamy {
    background-image: url("@/assets/img/foundation/light-creamy.svg");
  }

  &--foundation--light-tomato {
    background-image: url("@/assets/img/foundation/light-tomato.svg");
  }
}

</style>