<script setup lang="ts">

defineProps({
  value: { type: String, required: true },
  index: { type: Number, required: false }
})

</script>

<template>
  <div class="w-[100px] h-[100px] border rounded cursor-pointer" :id="`${index}`">
    {{ value }}
  </div>
</template>