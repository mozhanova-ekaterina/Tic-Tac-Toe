<script setup lang="ts">

defineProps({
  value: { type: String, required: true },
  index: { type: Number, required: false }
})

</script>

<template>
  <div class="w-[100px] h-[100px] border rounded-xl cursor-pointer flex justify-center items-center text-4xl text-blue-300" :id="`${index}`">
    {{ value }}
  </div>
</template>