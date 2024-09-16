<script lang="ts" setup>
defineProps({
  winner: { type: String, required: false }
})

</script>

<template>
  <div v-if="winner" class="text-4xl text-green-500 text-center">
    The winner is {{ winner }} 
  </div>
  <div class="text-2xl text-center mb-10" v-else>
    Ничья
  </div>
</template>