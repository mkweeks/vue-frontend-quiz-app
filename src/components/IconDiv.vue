<template>
  <div class="icon-div">
    <h3>{{letter}}</h3>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "IconDiv",
  props: ["image", "letter"],
});
</script>

<style scoped>
.icon-div {
  width: 35px;
  height: 35px;
  border-radius: 5px;
  margin: auto 15px;
  background-color: #F4F6FA;
  float: left;
  display: flex;
  justify-content: center;
  align-items: center;
}

.icon-div :hover {
  background-color: rgb(167, 41, 245)
}

h3 {
  font-family: "rubik regular"
}
</style>
