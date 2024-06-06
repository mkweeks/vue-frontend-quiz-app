<template>
  <div class="menu">
    <div class="heading">
      <h1><span style="font-weight: 1">Quiz completed</span></h1>
      <h1>You scored...</h1>
    </div>
    <div class="disp-score">
      <div class="score">
        <div class="topic">
          <IconDiv></IconDiv><h2>Accessibility</h2>
        </div>
        <!-- <h1>{{score}}</h1> -->
        <h1><span style='font-size: 100px'>8</span></h1>
        <p>out of 10</p>
      </div>
      <button class="new-round" @click="newRound">Play Again</button>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import IconDiv from "@/components/IconDiv.vue";

export default defineComponent({
  name: "ScoreView",
  components: {
    IconDiv
  }, 
  methods: {
    newRound() {
        this.$router.push('/')
    }
  }
});
</script>

<style scoped>
h6 {
  font-family: "rubik";
}

.score {
  width: 450px;
  background-color: white;
  height: 450px;
  border-radius: 15px;
  box-shadow: 2px 2px 5px lightgray;
}

.heading {
  width: 550px;
  position: relative;
  bottom: 50px;
}

.menu {
  position: relative;
  display: flex;
  justify-content: space-between;
  height: 540px;
  width: 1160px;
  top: 50px;
}

.topic {
    display: flex;
    align-items: center;
}

.disp-score {
  display: flex;
  justify-content: space-between;
  flex-direction: column;
  height: 400px;
  width: fit-content;
  align-items: center;
}

button {
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

.score {
  display: flex;
  align-items: center;
  justify-content: space-evenly;
  flex-direction: column;
}
</style>
