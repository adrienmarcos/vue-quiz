<template>
  <div class="ctr">
    <transition name="fade" mode="out-in">
      <questions 
        v-if="questionsAnswered < questions.length" 
        :questions="questions" 
        :questionsAnswered="questionsAnswered" 
        @question-answered="questionAnswered"
      />

      <result v-else :results="results" :totalCorrect="totalCorrect" />
    </transition>

    <button 
      type="button" 
      class="reset-btn" 
      @click.prevent="reset" 
      v-if="questionsAnswered === questions.length"
    >
      Reiniciar
    </button>
  </div>
</template>

<style scoped>
</style>

<script lang="ts">
import Questions from './components/Questions.vue'
import Result from './components/Result.vue'

export default {
  name: 'app',
  components: {
    Questions, Result
  },
  data () {
    return {
      questionsAnswered: 0,
      totalCorrect: 0,
      questions: [
        {
          q: 'Quanto é 2 + 2?', 
          answers: [
            {
              text: '4',
              is_correct: true
            },
            {
              text: '3',
              is_correct: false 
            },
            {
              text: '8',
              is_correct: false 
            },
            {
              text: '5',
              is_correct: false 
            }
          ] 
        },
        { 
          q: 'Quantas letras tem a palavra "Banana"?', 
          answers: [
            {
              text: '5',
              is_correct: false
            },
            {
              text: '7',
              is_correct: false 
            },
            {
              text: '6',
              is_correct: true 
            },
            {
              text: '12',
              is_correct: false 
            }
          ] 
        },
        { 
          q: 'Encontre a letra faltando: B_lo', 
          answers: [
            {
              text: 'e',
              is_correct: false
            },
            {
              text: 'a',
              is_correct: false 
            },
            {
              text: 'i',
              is_correct: false 
            },
            {
              text: 'o',
              is_correct: true 
            }
          ] 
        },
      ],
      results: [
        {
          min: 0,
          max: 2,
          title: "Tente novamente!",
          desc: "Com um pouco mais de esforço você conseguirá!"
        },
        {
          min: 3,
          max: 3,
          title: "Muito bem!",
          desc: "Você realmente é muito inteligente!"
        }
      ]
    }
  },
  methods: {
    questionAnswered (is_correct: boolean): void {
      if (is_correct) this.totalCorrect++
      this.questionsAnswered++
    },
    reset (): void {
      this.questionsAnswered = 0
      this.totalCorrect = 0
    }
  }
}
</script>