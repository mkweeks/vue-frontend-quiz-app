<template>
  <button class="topic-container" @click="showTopic">
    <IconDiv></IconDiv>
    <div class="item-container">
      <h3>{{ quiz.title }}</h3>
    </div>
  </button>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import IconDiv from "./IconDiv.vue";

export default defineComponent({
  name: "MenuOptionItem",
  components: {
    IconDiv,
  },
  props: ["quiz"],
  methods: {
    showTopic() {
      this.$router.push(`quiz/${this.quiz.title}`);
      localStorage.setItem('quizTitle', this.quiz.title)
      localStorage.setItem("quizData", JSON.stringify(this.quiz.questions))
    },
  },
});
</script>

<style scoped>
.topic-container {
  position: relative;
  width: 450px;
  height: 80px;
  background-color: white;
  border: none;
  box-shadow: 2px 2px 5px lightgrey;
  border-radius: 15px;
  margin: 15px;
  display: flex;
  font-family: "rubik";
  font-size: 16px;
  color: #313e51;
}

.topic-container :hover {
  border: none
}

.item-container :hover {
  border: 1px solid green;
}

.item-container {
  width: 225px;
  display: flex;
  align-items: left;
}
</style>
