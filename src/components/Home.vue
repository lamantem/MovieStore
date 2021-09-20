<template>
  <ul class="cards">
    <li v-for="item in filteredList" :key="item.id" class="cards-item">
      <div class="card">
        <div>
          <b-button @click="addToFavorites(item)" id="fav-button">
            <font-awesome-icon
              class="fav-icon"
              :icon="['fas', 'heart']"
              transform="grow-6"
              fixed-width
            />
          </b-button>
          <img
            :src="'http://image.tmdb.org/t/p/w500' + item.poster_path"
            style="width: 100%"
          />
        </div>
        <h4 class="small-letters">{{ item.release_date }}</h4>
        <div>
          <h4 class="big-letters">
            <b>{{ item.title }}</b>
          </h4>
          <div class="rating-genre">
            <h4 class="small-letters">
              <b
                ><font-awesome-icon
                  class="navicon"
                  :icon="['fas', 'star']"
                  fixed-width
                />{{ item.vote_average }}</b
              >
            </h4>
            <h4 class="small-letters">Genero</h4>
          </div>
          <h4 class="small-letters">R$ {{ cost }}</h4>
          <b-btn @click="addToShoppingCart(item)" class="button"
            >Adicionar</b-btn
          >
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
      movieDataSource: [],
      cost: 120.32,
      transferVariable: [],
    };
  },
  props: {
    search: String,
  },
  components: {},
  beforeMount() {
    this.loadMovies();
    this.search = "";
  },
  computed: {
    filteredList() {
      return this.movieDataSource.filter((movie) => {
        return movie.title.toLowerCase().includes(this.search.toLowerCase());
      });
    },
  },
  methods: {
    loadMovies() {
      axios
        .get(
          "http://api.themoviedb.org/3/discover/movie?api_key=77853655fb4cb264407715947ab783cc"
        )
        .then((res) => {
          this.movieDataSource = res.data.results;
        })
        .catch((error) => {
          console.log(error);
        });
    },
    addToShoppingCart(item) {
      this.transferVariable = {
        title: item.title,
        cost: this.cost,
        poster_path: item.poster_path,
      };
      this.$emit("addToShoppingCart", this.transferVariable);
    },
    addToFavorites(item) {
      this.transferVariable = {
        title: item.title,
        cost: this.cost,
        poster_path: item.poster_path,
      };
      this.$emit("addToFavorite", this.transferVariable);
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
  padding: 75px 0 0 0;
  place-content: center;
}

.cards-item {
  display: flex;
  padding: 1rem;
  width: 400px;
}

.card {
  background-color: white;
  border-radius: 0.25rem;
  box-shadow: 0 20px 40px -14px rgba(0, 0, 0, 0.25);
  display: flex;
  flex-direction: column;
  overflow: hidden;
}

.fav-icon {
  color: #f6b93b;
  position: absolute;
  right: 5px;
  top: 5px;
}

#fav-button {
  position: absolute;
  right: 5px;
  top: 5px;
  background: none;
  height: 25px;
  width: 30px;
}

.big-letters {
  font-size: 16px;
}

.small-letters {
  font-size: 12px;
  margin: 0 2px;
}

.navicon {
  color: #f6b93b;
}

.rating-genre {
  display: flex;
  justify-content: center;
}

.button {
  width: 100%;
  background-color: #78e08f;
}

.btn-primary:hover,
.btn-primary:focus,
.btn-primary:active,
.btn-primary:active:focus:not(:disabled):not(.disabled),
.btn-secondary,
.btn:focus,
.btn:active,
.btn:hover {
  box-shadow: none !important;
  border: 0 !important;
  background-color: #78e08f;
  outline: 0;
}
</style>
