<script lang="ts" setup>
defineProps({
  winner: { type: String, required: false }
})

</script>

<template>
  <div class="border rounded-xl grow flex items-center justify-center text-lg text-center text-blue-400">
    <div v-if="winner">
      The winner is
      <div class="text-orange-400">{{ winner }}</div>
    </div>
    <div class="" v-else>
      Ничья
    </div>
  </div>
</template>