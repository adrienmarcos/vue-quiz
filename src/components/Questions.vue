<template>
  <div class="questions-ctr">
    <div class="progress">
      <div class="bar"></div>
      <div class="status">1 out of 3 questions answered</div>
    </div>

    <div class="single-question" v-for="question in questions" :key="question.q">
      <div class="question">{{ question.q }}</div>
      <div class="answers">
        <div class="answer" v-for="answer in question.answers" :key="answer.text">
          {{ answer.text }}
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
export default {
  props: ['questions'],
  name: 'questions',
  data () {
    return {
      
    }
  }
}
</script>

<style></style>