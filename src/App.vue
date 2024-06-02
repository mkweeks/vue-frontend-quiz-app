<template>
  <div class="main">
    <NavBar :item="quizzes"></NavBar>
    <router-view />
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import quizzes from "../src/data.json";
import NavBar from "./components/NavBar.vue";

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
  data(): quizData {
    return quizzes;
  },
  methods: {},

  components: {
    NavBar,
  },
});
</script>

<style scoped>
@font-face {
  font-family: "rubik italic";
  src: url(../src/assets/fonts/static/Rubik-Italic.ttf);
}

@font-face {
  font-family: "rubik regular";
  src: url(../src/assets/fonts/static/Rubik-Regular.ttf);
}

.main {
  width: 100%;
  height: 100vh;
  font-family: "rubik regular";
  color: #313e51;
  background-image: url("./assets/images/pattern-background-desktop-light.svg");
  background-repeat: no-repeat;
  background-size: cover;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

body {
  margin: 0px;
}
</style>
