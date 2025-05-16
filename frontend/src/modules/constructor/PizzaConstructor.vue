<template>
  <app-drop>
    <div class="pizza pizza--foundation--big-tomato">
      <div class="pizza__wrapper">
        <div class="pizza__filling pizza__filling--ananas"></div>
        <div class="pizza__filling pizza__filling--bacon"></div>
        <div class="pizza__filling pizza__filling--cheddar"></div>
      </div>
    </div>
  </app-drop>
</template>

<script setup>
import AppDrop from "../../common/components/AppDrop.vue";

defineEmits(['drop'])
</script>

<style scoped lang="scss">

</style>