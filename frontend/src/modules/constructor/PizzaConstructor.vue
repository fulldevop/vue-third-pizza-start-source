<template>
  <app-drop>
    <div class="pizza pizza--foundation--big-tomato">
      <div class="pizza__wrapper">
        <template v-for="(value, key, index) in ingredients"
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
const props = defineProps({
  ingredients: {
    type: Object,
    required: true
  }
})

defineEmits(['drop'])
</script>

<style scoped lang="scss">

</style>