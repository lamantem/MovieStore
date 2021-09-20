<template>
  <div id="app">
    <Header
      :shoppingCart="this.shoppingCart"
      :favorites="this.favorites"
      @searchingMovies="searching()"
      @toggleCheckout="toggleCheckoutView"
      @backHome="backHome"
    >
    </Header>
    <Checkout
      v-if="toggleCheckout"
      @toggleCheckout="toggleCheckoutView"
    ></Checkout>
    <Home
      v-if="!toggleCheckout"
      :search="this.search"
      @addToShoppingCart="addToShoppingCart"
      @addToFavorite="addToFavorites"
    >
    </Home>
  </div>
</template>

<script>
import Home from "./components/Home.vue";
import Checkout from "./components/Checkout.vue";
import Header from "./shared/Header.vue";

export default {
  name: "App",
  data() {
    return {
      shoppingCart: Array,
      favorites: Array,
      search: String,
      toggleCheckout: Boolean,
    };
  },
  components: {
    Home,
    Header,
    Checkout,
  },
  beforeMount() {
    this.shoppingCart = [];
    this.favorites = [];
    this.favorites = [];
    this.toggleCheckout = false;
  },
  methods: {
    addToShoppingCart(item) {
      this.shoppingCart.push(item);
    },
    addToFavorites(item) {
      this.favorites.push(item);
    },
    searching() {
      this.search = event.target.value;
    },
    toggleCheckoutView() {
      this.toggleCheckout = !this.toggleCheckout;
    },
    backHome() {
      this.toggleCheckout = false;
    }
  },
};
</script>

<style>
@import "~bootstrap-vue/dist/bootstrap-vue.min.css";
body {
  margin: 0;
}

html,
body {
  height: auto;
}

#app {
  height: auto;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.b-sidebar {
  margin-top: 64px !important;
}

.btn {
  border-radius: 0;
  transition: none !important;
}

.btn-primary:hover,
.btn-primary:focus,
.btn-primary:active,
.btn-primary:active:focus:not(:disabled):not(.disabled),
.btn:focus,
.btn:active,
.btn:hover {
  box-shadow: none !important;
  background-color: #1e3799 !important;
  outline: 0;
}
</style>
