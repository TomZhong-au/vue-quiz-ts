<template>
  <div>
    this is test component
    {{ props.title }}
    {{ props.body }}
  </div>
</template>

<script setup lang="ts">
export interface Props {
  title: string
  body?: string
}

const props = defineProps<Props>()
</script>

<style scoped></style>
