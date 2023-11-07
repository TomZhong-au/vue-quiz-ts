<template>
  <div>
    <div class="result">
      <div class="title">{{ props.data.title }}</div>
      <div class="desc">{{ props.data.desc }}</div>
    </div>
    <button type="button" class="reset-btn" @click="$emit('reset')">Reset</button>
  </div>
</template>

<script setup lang="ts">
export interface Props {
  data: {
    title: string
    desc?: string
  }
}
const props = defineProps<Props>()
defineEmits(['reset'])
</script>

<script lang="ts">
export default {
  name: 'FinalResult'
}
</script>

<style scoped></style>
