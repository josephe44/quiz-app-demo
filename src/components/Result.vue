<template>
  <div class="result">
    <div class="title">You got {{ totalCorrect }} out {{ questionLength }}</div>
    <div class="title">{{ results[resultIndex].title }}</div>
    <div class="desc">{{ results[resultIndex].desc }}</div>
  </div>
</template>

<script>
export default {
  name: "Result",
  props: {
    results: {
      type: Object,
      required: true,
    },
    totalCorrect: {
      type: Number,
      required: true,
    },
    questionLength: {
      type: Number,
      required: true,
    },
  },
  computed: {
    resultIndex() {
      let index = 0;
      this.results.forEach((e, i) => {
        if (e.min <= this.totalCorrect && e.max >= this.totalCorrect) {
          index = i;
        }
      });

      return index;
    },
  },
};
</script>

<style lang="scss" scoped></style>
