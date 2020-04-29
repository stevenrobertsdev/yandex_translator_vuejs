<template>
  <h3 class="title">{{title}}</h3>
</template>

<script>
export default {
  name: "Title",
  props: {
    title: String
  }
};
</script>

<style scoped>
.title {
  text-align: center;
  font-size: 42px;
  color: #ffffff;
  margin-top: 40px;
  font-weight: 700;
  margin: 40px 0;
}
</style>