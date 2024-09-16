<script lang="ts" setup>
const emit = defineEmits(['restart'])
</script>
<template>
  <div class="text-center">
    <button class="border px-2 py-1 rounded-xl text-2xl text-green-500 hover:text-orange-400" @click="emit('restart')">
      Начать заново
    </button>
  </div>
</template>