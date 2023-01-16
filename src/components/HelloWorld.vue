<template>
  <div class="hello-world">
    <h1>{{ msg }}</h1>
    <button @click="loadQuestions">Load</button>
    <div>{{ questions }}</div>
  </div>
</template>

<script setup lang="ts">
  import { ref } from "vue";

  defineProps<{ msg: string }>();

  const count = ref(0);
  const questions = ref([]);

  const loadQuestions = async () => {
    const result = await fetch("https://opentdb.com/api.php?amount=10");
    questions.value = result.text;
    console.log("result:", result);
  };
</script>

<style scoped>
  h1 {
    margin-top: 100px;
    background-color: red;
  }
</style>
