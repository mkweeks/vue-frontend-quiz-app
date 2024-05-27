<template>
  <div class="main">
    <NavBar :item="quizzes"></NavBar>
    <div class="menu">
      <div class="heading">
        <h1><span style="font-weight: 1;">Welcome to the</span> Frontend Quiz!</h1>
        <h6>Pick a subject to get started</h6>
      </div>
      <div class="options">
        <MenuOptionItem :quiz="quiz" v-for="quiz in quizzes" :key=quiz.title @button-clicked="showTopic"></MenuOptionItem>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import quizzes from '../src/data.json';
import MenuOptionItem from '../src/components/MenuOptionItem.vue';
import NavBar from './components/NavBar.vue';

interface quizData {
  quizzes: {
    title: string;
    icon: string;
    questions: {
      question: string;
      options: string[];
    }[];
  }[]
}

export default defineComponent({
  data(): quizData {
    return quizzes;
  },
  methods: {
    showTopic(payload: any){
      console.log(payload)
    }
  },

  components: {
    MenuOptionItem,
    NavBar,
  },
})

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
  color: #313E51;
  background-image: url('./assets/images/pattern-background-desktop-light.svg');
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
  height: fit-content;
  width: 1160px;
  margin-bottom: 10%;
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
  border: 3px solid #A729F5;
}
</style>
