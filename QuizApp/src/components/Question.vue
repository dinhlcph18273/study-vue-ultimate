<script setup>
import { defineProps, defineEmits } from "vue";

const emit = defineEmits(["selectOption"]);

const { question } = defineProps(["question"]);

const emitSelectOption = (isCorrect) => {
  emit("selectOption", isCorrect);
};
</script>

<template>
  <div>
    <div class="question-container">
      <h1 class="question">{{ question.text }}</h1>
    </div>
    <div class="answers-container">
      <div
        class="option"
        v-for="(option, index) in question.options"
        :key="index"
        @click="emitSelectOption(option.isCorrect)"
      >
        <div class="option-label">{{ option.label }}</div>
        <div class="option-value">{{ option.text }}</div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.question-container {
  margin-top: 20px;
}

.question {
  font-size: 40px;
  margin-bottom: 20px;
}

.option {
  display: flex;
  margin-bottom: 20px;
  cursor: pointer;
}

.option-label {
  background-color: bisque;
  width: 50px;
  height: 50px;
  font-size: 30px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.option-value {
  background-color: rgb(244, 239, 239);
  width: 100%;
  font-size: 30px;
  padding: 0 20px;
  display: flex;
  align-items: center;
}
</style>
