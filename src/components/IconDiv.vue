<template>
    <div class="icon-div">
        <!-- <img :src='item.icon' > -->
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    name: "IconDiv",
    props: ["item"]
})
</script>

<style scoped>
.icon-div {
    width: 45px;
    height: 45px;
    border-radius: 10px;
    margin: auto 15px;
    background-color: lightblue;
    float: left;
}

</style>