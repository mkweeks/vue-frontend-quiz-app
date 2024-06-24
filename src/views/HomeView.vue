<template>
  <div class="menu">
    <div class="heading">
      <h1><span style="font-weight: 1">Welcome to the</span> Frontend Quiz!</h1>
      <h6>Pick a subject to get started</h6>
    </div>
    <div class="options">
      <MenuOptionItem :quiz="quiz" v-for="quiz in quizzes" :key="quiz.title"></MenuOptionItem>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import quizzes from "../data.json";
import MenuOptionItem from "../components/MenuOptionItem.vue";

interface quizData {
  quizzes: {
    title: string;
    icon: string;
    questions: {
      question: string;
      options: string[];
    }[];
  }[];
}

export default defineComponent({
  name: "HomeView",
  data(): quizData {
    return quizzes;
  },
  components: {
    MenuOptionItem,
  },
});
</script>

<style scoped>
.heading {
  width: 550px;
}

.options {
  width: fit-content;
  height: 340px;
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
}

h1 {
  font-family: "rubik regular";
  font-size: 64px;
}

h6 {
  font-family: "rubik italic";
  font-size: 12px;
}

.options :hover {
  border: 3px solid #a729f5;
}
</style>
