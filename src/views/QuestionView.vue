<template>
  <div class="menu">
    <div class="heading">
      <div class="questionNumber">Question {{ currentQuestion }} of 10</div>
      <h2>{{ questionSet[increment].question }}</h2>
    </div>
    <div class="options">
      <button class="choice"><IconDiv letter="A"></IconDiv>{{ options[0] }}</button>
      <button class="choice"><IconDiv letter="B"></IconDiv>{{ options[1] }}</button>
      <button class="choice"><IconDiv letter="C"></IconDiv>{{ options[2] }}</button>
      <button class="choice"><IconDiv letter="D"></IconDiv>{{ options[3] }}</button>
      <button class="submit" @click="checkAnswer">Submit Answer</button>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import IconDiv from "@/components/IconDiv.vue";

export default defineComponent({
  name: "QuestionView",
  components: {
    IconDiv
  },
  methods: {
    checkAnswer() {
      this.increment ++;
      this.currentQuestion ++;
      this.options = this.questionSet[this.increment].options
    },
  },
  data(): any {
    return {
      receivedObject: {},
      currentQuestion: 1,
      increment: 0,
      questionSet: [],
      options: [],
    };
  },
  created() {
    const questionSet = localStorage.getItem("quizData");
    if (questionSet) {
      this.questionSet = JSON.parse(questionSet);
      this.options = this.questionSet[this.increment].options;
    }
  },
});
</script>

<style scoped>
.submit {
  position: relative;
  width: 450px;
  height: 80px;
  background-color: #A729F5;
  border: none;
  box-shadow: 2px 2px 5px lightgrey;
  border-radius: 15px;
  margin: 15px;
  align-items: center;
  font-family: "rubik";
  font-size: 16px;
  color: white;
}

.heading {
  display: flex;
  flex-direction: column;
  width: 550px;
  margin-top: 0px;
}

.questionNumber {
  font-family: "rubik italic";
  margin-top: 0px;
}

.options {
  width: fit-content;
  height: 405px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.options :hover {
  border: solid #a729f5;
}

.menu {
  display: flex;
  justify-content: space-between;
  height: fit-content;
  width: 1160px;
  margin-top: 25px;
}

.choice {
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
  align-items: center;
}
</style>
