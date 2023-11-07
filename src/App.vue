<template>
  <div class="ctr">
    <div class="questions-ctr">
      <div class="progress">
        <ProgressBar :width="questionsAnswered / questions.length" />
        <div class="status">{{ questionsAnswered }} out of 3 questions answered</div>
      </div>
    </div>

    <Transition name="fade" mode="out-in">
      <Question
        :questionData="questions[questionsAnswered]"
        v-if="questionsAnswered < questions.length"
        @chooseAnswer="handleChooseAnswer"
        :key="questions[questionsAnswered].q"
      />

      <Result :data="result" v-else @reset="handleReset" key="result" />
    </Transition>
    <test />
  </div>
</template>

<script setup lang="ts">
import ProgressBar from './components/ProgressBar.vue'
import Question from './components/Question.vue'
import Result from './components/Result.vue'
import { ref, computed } from 'vue'
import { data } from './data'
import { results } from './data'
import test from './components/Test.vue'

const questionsAnswered = ref(0)
const correctAnswersCount = ref(0)

const questions = data.questions
const result = computed(() => {
  return correctAnswersCount.value === questions.length ? results[1] : results[0]
})

const handleChooseAnswer = (isCorrect: boolean) => {
  if (isCorrect) {
    correctAnswersCount.value++
  }
  questionsAnswered.value++
}

function handleReset() {
  questionsAnswered.value = 0
  correctAnswersCount.value = 0
}
</script>

<style scoped></style>
