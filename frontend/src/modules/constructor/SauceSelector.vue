<template>
  <div class="ingredients__sauce">
    <p>Основной соус:</p>

    <label
      v-for="sauce in sauceItems"
      :key="sauce.id"
      class="radio ingredients__input"
    >
      <input
        type="radio"
        name="sauce"
        :value="sauce.value"
        checked
      />
      <span>{{ sauce.name }}</span>
    </label>
  </div>
</template>

<script setup>
import saucesJSON from "@/mocks/sauces.json";
import { normalizeSauce } from "@/common/normalize";

const sauceItems = saucesJSON.map(normalizeSauce);
</script>

<style scoped lang="scss">

</style>