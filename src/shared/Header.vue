<template>
  <div class="header">
    <div id="column1">
      <b-button @click="$emit('backHome')">
        <font-awesome-icon
          class="logo icon-spacing"
          :icon="['fas', 'film']"
          transform="grow-36"
          fixed-width
        />
      </b-button>
    </div>

    <div id="column2">
      <input
        v-on:input="searching()"
        class="search-field"
        v-model="search"
        type="text"
      />
      <font-awesome-icon
        class="logo icon-spacing search-icon"
        :icon="['fas', 'search']"
        transform="grow-7"
        fixed-width
      />
    </div>

    <div id="column3">
      <Favorites
        @clearFavoritesList="$emit('clearFavoritesList')"
        :favoritesList="this.favorites"
      ></Favorites>
      <ShoppingCart
        :shoppingCartList="this.shoppingCart"
        @toggleCheckout="toggleChecksdso"
        @clearCheckoutList="$emit('clearCheckoutList')"
      ></ShoppingCart>
    </div>
  </div>
</template>

<script>
import ShoppingCart from "../components/ShoppingCart.vue";
import Favorites from "../components/Favorites.vue";

export default {
  name: "Header",
  data() {
    return {
      favSidebarIsOpen: false,
      shopSidebarIsOpen: false,
      search: "",
    };
  },
  props: {
    favorites: Array,
    shoppingCart: Array,
  },
  beforeMount() {
    this.search = "a";
    this.search = "";
  },
  components: {
    ShoppingCart,
    Favorites,
  },
  methods: {
    searching() {
      this.$emit("searchingMovies", this.search);
    },
       toggleChecksdso() {
      this.$emit('toggleCheckout', this.shoppingCart);
    }
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.header {
  padding: 14px;
  background-color: #1e3799;
  overflow: hidden;
  display: flex;
  position: fixed;
  width: 100%;
  z-index: 200;
}

.header > div {
  flex-grow: 1;
}

#column1,
#column3 {
  width: 30%;
  display: inline-block;
}

#column2 {
  width: 40%;
  display: inline-block;
  display: flex;
  justify-content: center;
  align-items: baseline;
}

#column3 {
  display: inline-flex;
}

.search-field {
  border-radius: 5px;
  width: 100%;
}

.logo {
  float: left;
}

.navicon {
  float: right;
}

.search-icon {
  position: absolute;
  top: 21px;
  right: 35%;
}

button {
  background-color: #1e3799;
  border: 0;
}
</style>
