<template>
  <div class="result">
    <div class="title">{{ results[resultIndex].title }}</div>
    <div class="desc">{{ results[resultIndex].desc }}</div>
  </div>
</template>

<script lang="ts">
export default {
  props: ['results', 'totalCorrect'],
  name: 'result',
  computed: {
    resultIndex (): number {
      let index = 0
      this.results.forEach((e: any, i: any) => {
        if (e.min <= this.totalCorrect && e.max >= this.totalCorrect) {
          index = i
        }
      })
      return index
    }
  }
}
</script>