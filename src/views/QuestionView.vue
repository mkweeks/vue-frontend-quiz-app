<template>
  <div class="menu">
    <div class="heading">
      <div class="questionNumber">Question {{ currentQuestion }} of 10</div>
      <h2>{{ questionSet[increment].question }}</h2>
    </div>
    <div class="options">
      <button
        :disabled="isCorrect"
        class="choice"
        :class="{
          correct: correctAnswer == options[0] && correctAnswer == selectedAnswer,
          wrong: correctAnswer !== selectedAnswer && selectedAnswer == options[0],
        }"
        @click="selected(options[0])"
      >
        <IconDiv letter="A"></IconDiv>{{ options[0] }}
      </button>
      <button
        :disabled="isCorrect"
        class="choice"
        :class="{
          correct: correctAnswer == options[1] && correctAnswer == selectedAnswer ,
          wrong: correctAnswer !== selectedAnswer && selectedAnswer == options[1],
        }"
        @click="selected(options[1])"
      >
        <IconDiv letter="B"></IconDiv>{{ options[1] }}
      </button>
      <button
        :disabled="isCorrect"
        class="choice"
        :class="{
          correct: correctAnswer == options[2] && correctAnswer == selectedAnswer,
          wrong: correctAnswer !== selectedAnswer && selectedAnswer == options[2],
        }"
        @click="selected(options[2])"
      >
        <IconDiv letter="C"></IconDiv>{{ options[2] }}
      </button>
      <button
        :disabled="isCorrect"
        class="choice"
        :class="{
          correct: correctAnswer == options[3] && correctAnswer == selectedAnswer,
          wrong: correctAnswer !== selectedAnswer && selectedAnswer == options[3],
        }"
        @click="selected(options[3])"
      >
        <IconDiv letter="D"></IconDiv>{{ options[3] }}
      </button>
      <button class="submit" @click="checkAnswer">Submit Answer</button>
    </div>
  </div>
  <div class="no-answer" v-show="show"><p style="color: #EE5454">Please select an answer</p></div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import IconDiv from "@/components/IconDiv.vue";

export default defineComponent({
  name: "QuestionView",
  components: {
    IconDiv,
  },
  methods: {
    checkAnswer() {
      if (this.currentQuestion < 10 && this.selectedAnswer !== "") {
        this.increment++;
        this.currentQuestion++;
        this.selectedAnswer = ""

        this.options = this.questionSet[this.increment].options;
        this.correctAnswer = this.questionSet[this.increment].answer;
        this.isCorrect = false;
      } else if (this.selectedAnswer === "") {
        this.show = true
      }
      else {
        localStorage.setItem("finalScore", this.score);
        this.$router.push(`score`);
      }
    },
    selected(option: string) {
      this.selectedAnswer = option;
      this.show = false
      console.log(this.selectedAnswer);
      if (this.selectedAnswer == this.correctAnswer) {
        this.score++;
        this.isCorrect = true;
      }
      else {
        this.isCorrect = true
      }
    },
  },
  data(): any {
    return {
      currentQuestion: 1,
      increment: 0,
      questionSet: [],
      options: [],
      selectedAnswer: "",
      correctAnswer: "",
      score: 0,
      isCorrect: false,
      show: false,
    };
  },
  created() {
    const questionSet = localStorage.getItem("quizData");
    if (questionSet) {
      this.questionSet = JSON.parse(questionSet);
      this.options = this.questionSet[this.increment].options;
      this.correctAnswer = this.questionSet[this.increment].answer;
    }
  },
});
</script>

<style scoped>
.submit {
  position: relative;
  width: 450px;
  height: 80px;
  background-color: #a729f5;
  border: none;
  box-shadow: 2px 2px 5px lightgrey;
  border-radius: 15px;
  margin: 15px;
  align-items: center;
  font-family: "rubik";
  font-size: 16px;
  color: white;
}

.correct {
  border: 3px solid #26D782 !important;
}

.wrong {
  border: 3px solid #EE5454 !important;
}

.heading {
  width: 550px;
}

.questionNumber {
  font-family: "rubik italic";
}

.options {
  width: fit-content;
  height: 405px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  margin: 15px;
}

.menu {
  display: flex;
  justify-content: space-between;
  height: 540px;
  width: 1160px;
  position: relative;
  top: 50px;
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
