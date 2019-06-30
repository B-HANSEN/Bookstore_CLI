`<template>
  <div id="container" class="d-flex flex-wrap justify-content-around">
    <div class="flip-card" v-for="book in filteredBooks" v-bind:key="book">
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
</template>

<script>
export default {
  components: {
    props: { books }
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
  margin-top: 250px;
  /* font-family: Arial, Helvetica, sans-serif; */
  background-color: #fdf7f7;
}
img {
  width: 60%;
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
