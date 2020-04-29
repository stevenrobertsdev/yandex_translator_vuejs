<template>
  <div>
    <Title title="YANDEX API TRANSLATOR 2.0" />
    <Window />
  </div>
</template>

<script>
import Title from "./components/Title";
import Window from "./components/Window";

export default {
  name: "App",
  components: {
    Title,
    Window,
  },
};
</script>

<style>
@import "./app.css";
</style>
