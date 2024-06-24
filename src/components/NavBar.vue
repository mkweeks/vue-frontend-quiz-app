<template>
  <div class="toggle-theme">
    <div class="toggle">
      <img src="@/assets/images/icon-sun-dark.svg" />
      <label class="switch">
        <input type="checkbox" />
        <span class="slider round"></span>
      </label>
      <img src="@/assets/images/icon-moon-dark.svg" />
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "NavBar",
  components: {
    // IconDiv,
  },
  props: ["item"],
  data() {
    return {};
  },
});
</script>

<style scoped>
.toggle-theme {
  width: 100vw;
  height: 50px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.toggle {
  display: flex;
  margin-left: 85%;
  position: fixed;
}


.switch {
  position: relative;
  height: 30px;
  width: 58px;
  display: inline-block;
}

.switch input {
  opacity: 0;
  width: 0;
  height: 0;
}

.slider {
  position: absolute;
  cursor: pointer;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: #a729f5;
  -webkit-transition: 0.4s;
  transition: 0.4s;
}

.slider:before {
  position: absolute;
  content: "";
  height: 24px;
  width: 24px;
  left: 4px;
  bottom: 3px;
  background-color: white;
  -webkit-transition: 0.4s;
  transition: 0.4s;
}

input:checked + .slider {
  background-color: #a729f5;
}

input:focus + .slider {
  box-shadow: 0 0 1px #a729f5;
}

input:checked + .slider:before {
  -webkit-transform: translateX(26px);
  -ms-transform: translateX(26px);
  transform: translateX(26px);
}

/* Rounded sliders */
.slider.round {
  border-radius: 34px;
}

.slider.round:before {
  border-radius: 50%;
}
</style>
