`<template>
  <div id="app">
    <app-bookstore v-bind:books="json"></app-bookstore>
  </div>
</template>

<script>
import bookstore from "./components/bookstore.vue";

export default {
  name: "app",
  components: {
    "app-bookstore": bookstore
  },
  data() {
    return {
      json: []
    };
  },
  created: function() {
    fetch("https://api.myjson.com/bins/1h3vb3")
      .then(r => r.json())
      .then(json => {
        console.log(json.books);
        this.json = json.books;
      });
  }
};
</script>

<style>
body {
  font-family: "Nunito SemiBold";
}
</style>