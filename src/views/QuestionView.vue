<template>
  <div class="menu">
    <div class="heading">
      <div class="questionNumber">Question {{ currentQuestion }} of 10</div>
      <h2>{{ questionSet[increment].question }}</h2>
    </div>
    <div class="options">
      <button class="choice" @click="selected(options[0])">
        <IconDiv letter="A"></IconDiv>{{ options[0] }}
      </button>
      <button class="choice" @click="selected(options[1])">
        <IconDiv letter="B"></IconDiv>{{ options[1] }}
      </button>
      <button class="choice" @click="selected(options[2])">
        <IconDiv letter="C"></IconDiv>{{ options[2] }}
      </button>
      <button class="choice" @click="selected(options[3])">
        <IconDiv letter="D"></IconDiv>{{ options[3] }}
      </button>
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
    IconDiv,
  },
  methods: {
    checkAnswer() {
      if (this.currentQuestion < 10) {
        this.increment++;
        this.currentQuestion++;

        this.options = this.questionSet[this.increment].options;
        this.correctAnswer = this.questionSet[this.increment].answer;
      } else {
        this.$router.replace("score");
      }
    },
    selected(option: string) {
      this.selectedAnswer = option;
      if (this.selectedAnswer == this.correctAnswer) {
        this.score++;
        console.log(this.score);
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
}

.options :hover {
  border: solid #a729f5;
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
