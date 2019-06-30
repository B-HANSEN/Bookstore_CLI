`<template>
  <header id="header">
    <img src="../../src/assets/screenshot_new.png" alt="logo" />
    <input type="text" class="searchfield" v-model="search" placeholder="Search..." />
  </header>
</template>

<script>
export default {
  components: {
    props: { books }
  },
  data() {
    return {
      search: ""
    };
  },
  computed: {
    filteredBooks: function() {
      return this.books.filter(book => {
        return book.titulo.toLowerCase().includes(this.search.toLowerCase());
      });
    }
  }
};
</script>

<style>
header {
  padding-bottom: 30px;
  border: 1px dashed lightgrey;
  background-color: #fdf7f7 !important;
  display: flex;
  justify-content: space-between;
  position: fixed;
  top: 0;
}

.logo {
  width: 500px;
  padding-left: 50px;
  padding-top: 20px;
}

.searchDiv {
  padding: 100px 40px 0px 0px;
}

.searchfield {
  width: 300px;
  height: 50px;
  padding: 10px;
}
</style>
