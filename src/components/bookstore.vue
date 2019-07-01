`<template>
  <div>
    <header>
      <img src="../../src/assets/screenshot_new.png" class="logo_img" alt="logo" />
      <div class="searchDiv">
        <input type="text" class="searchfield" v-model="search" placeholder="Search..." />
      </div>
    </header>

    <div id="container" class="d-flex flex-wrap justify-content-around">
      <div class="flip-card" v-for="(book,i) in filteredBooks" v-bind:key="i" :data-index="i">
        <div class="flip-card-intermediate">
          <div class="flip-card-inner">
            <div class="flip-card-front">
              <img :src="book.portada" />
            </div>
            <div class="flip-card-back">
              <h5>{{ book.titulo }}</h5>
              <p>{{ book.descripcion }}</p>
              <a data-fancybox="gallery" :href="book.detalle">
                <button>more info</button>
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  components: {},
  props: ["books"],
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
  padding-left: 50px;
  padding-top: 20px;
}

.logo_img {
  width: 30%;
}

img {
  width: 60%;
}

.searchDiv {
  padding: 10px 20px 0px 0px;
}

.searchfield {
  width: 300px;
  height: 20px;
  padding: 10px;
}

body {
  margin-top: 250px;
  /* font-family: Arial, Helvetica, sans-serif; */
  background-color: #fdf7f7;
}

#container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}

.flip-card {
  background-color: transparent;
  height: 300px;
  width: 300px;
  perspective: 1000px;
}
.flip-card-inner {
  border: 1px groove black;
  display: flex;
  flex-flow: row wrap;
  position: relative;
  width: 300px;
  text-align: center;
  transition: transform 0.6s;
  transform-style: preserve-3d;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
}
.flip-card:hover .flip-card-inner {
  transform: rotateY(180deg);
}
.flip-card-front,
.flip-card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  backface-visibility: hidden;
}
.flip-card-front {
  background-color: #bbb;
  color: black;
}
.flip-card-back {
  color: black;
  transform: rotateY(180deg);
  padding: 5px 30px 5px 30px;
  font-size: 12px;
}
</style>
