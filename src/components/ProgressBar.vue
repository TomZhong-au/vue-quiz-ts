<template>
  <div class="bar" :style="{ width: `${props.width * 100}%` }"></div>
</template>

<script lang="ts">
interface Props {
  width: number
}
</script>

<script setup lang="ts">
const props = defineProps<Props>()
</script>

<style scoped></style>
