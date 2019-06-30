`<template>
  <div>
    <app-header></app-header>
    <app-bookstore></app-bookstore>
  </div>
</template>

<script>
import header from "./components/header.vue";
import bookstore from "./components/bookstore.vue";

export default {
  components: {
    "app-header": header, // use app-header because <header></header> is already an html-tag
    "app-bookstore": bookstore
  }
};
</script>

<style>
body {
  margin: 0;
  font-family: "Nunito SemiBold";
}
</style>