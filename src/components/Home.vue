<template>
  <ul class="cards">
    <li v-for="item in filmDataSource" :key="item.id" class="cards-item">
      <div class="card">
        <img
          :src="'http://image.tmdb.org/t/p/w500' + item.poster_path"
          style="width: 100%"
        />
        <h4 class="small-letters">{{ item.release_date }}</h4>
        <div>
          <h4 class="big-letters">
            <b>{{ item.title }}</b>
          </h4>
          <div class="rating-genre">
            <h4 class="small-letters">
              <b>{{ item.vote_average }}</b>
            </h4>
            <h4 class="small-letters">\\\\Genero\\\\</h4>
          </div>
          <h4 class="small-letters">R$42210,00</h4>
          <b-btn @click="addToShoppingCart(item)">test</b-btn>
        </div>
      </div>
    </li>
  </ul>
</template>

<script>
import axios from "axios";

export default {
  name: "Home",
  data() {
    return {
      filmDataSource: [],
    };
  },
  components: {},
  beforeMount() {
    this.loadMovies();
    this.loadImages();
  },
  methods: {
    loadMovies() {
      axios
        .get(
          "http://api.themoviedb.org/3/discover/movie?api_key=77853655fb4cb264407715947ab783cc"
        )
        .then((res) => {
          this.filmDataSource = res.data.results;
          console.log(res.data);
          // console.log(this.filmDataSource);
        })
        .catch((error) => {
          console.log(error);
        });
    },
    decodeImage() {
      return axios
        .get("http://image.tmdb.org/t/p/w500/lSEr1nphZuCqXli3VziIgCI8Ivf.jpg", {
          responseType: "arraybuffer",
        })
        .then((response) =>
          new Buffer(response.data, "binary").toString("base64")
        );
    },
    addToShoppingCart(item) {
      this.$emit("addToShoppingCart", item);
    },
    addToFavorite(item) {
      this.$emit("addToFavorite", item);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.cards {
  display: flex;
  flex-wrap: wrap;
  list-style: none;
  margin: 0;
  padding: 0;
  place-content: center;
}

.cards-item {
  display: flex;
  padding: 1rem;
  width: 350px;
}

.card {
  background-color: white;
  border-radius: 0.25rem;
  box-shadow: 0 20px 40px -14px rgba(0, 0, 0, 0.25);
  display: flex;
  flex-direction: column;
  overflow: hidden;
}

.big-letters {
  font-size: 16px;
}

.small-letters {
  font-size: 12px;
}

.rating-genre {
  display: flex;
  justify-content: center;
}
</style>
