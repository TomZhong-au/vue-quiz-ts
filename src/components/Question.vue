<template>
  <div class="single-question">
    <div class="question">{{ props.questionData.q }}</div>
    <div class="answers">
      <div
        class="answer"
        v-for="answer in props.questionData.answers"
        :key="answer.text"
        @click="($event) => $emit('chooseAnswer', answer.is_correct)"
      >
        {{ answer.text }}
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
type Prop = {
  questionData: {
    id: string
    q: string
    answers: {
      text: string
      is_correct: boolean
    }[]
  }
}

const props = defineProps<Prop>()
</script>

<script lang="ts">
export default {
  name: 'QuizQuestion'
}
</script>
<style lang="scss" scoped></style>
