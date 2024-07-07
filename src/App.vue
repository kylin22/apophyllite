<script setup lang="ts">
  import ChapterNav from "./pages/ChapterNav.vue";
  import ChapterButton from "./components/ChapterButton.vue";
</script>

<template>
  <ChapterNav/>
</template>

<style lang="scss">
  #app {
    height: 100vh;
  }

  body {
    background-color: black;
  }

  body, html {
    user-select: none;
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    margin: 0;
    padding: 0;
    color: white;
    letter-spacing: 3px;
  }
</style>

