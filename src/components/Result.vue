<template>
  <div class="results">
    <h1>Your Reaction Time : {{ score }} ms</h1>
    <h3>{{ message }}</h3>
  </div>
</template>

<script>
export default {
  props: ["score"],
  data() {
    return {
      message: null,
    };
  },
  mounted() {
    this.updateMessage();
  },
  methods: {
    updateMessage() {
      if (this.score < 250) {
        this.message = "Perfect";
      } else if (this.score < 300) {
        this.message = "Good";
      } else if (this.score < 400) {
        this.message = "Slow !";
      } else {
        this.message = "You are slower than my grandmother !!";
      }
    },
  },
};
</script>

<style>
.results h3 {
  color: #0faf87;
}
</style>
