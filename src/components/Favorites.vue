<template>
  <div class="content">
    <b-button class="shadow-none" v-b-toggle.sidebar2-no-header>
      <font-awesome-icon
        class="navicon icon-spacing"
        :icon="['fas', 'heart']"
        transform="grow-6"
        fixed-width
      />
    </b-button>
    <b-sidebar
      id="sidebar2-no-header"
      title="Meus Favoritos"
      right
      no-header
      shadow
    >
      <div class="px-3 py-2">
        <div class="title-button">
          <p>Meus Favoritos</p>
          <b-button @click="$emit('clearFavoritesList')" class="clear-button"
            >Esvaziar</b-button
          >
        </div>
        <li v-for="item in favoritesList" :key="item.message">
          <img
            class="poster-images"
            :src="'http://image.tmdb.org/t/p/w500' + item.poster_path"
          />
          <span class="movie-title">`{{ TextAbstract(item.title, 11) }}</span>
          <span>R${{ item.cost }}</span>
          <b-button
            @click="$emit('addToShoppingFromFavorite', item)"
            id="shopping-button"
          >
            <font-awesome-icon
              class="fav-icon"
              :icon="['fas', 'shopping-cart']"
              transform="grow-2"
              fixed-width
            />
          </b-button>
          <font-awesome-icon
            class="navicon icon-spacing sidebar-action-icon"
            :icon="['fas', 'trash']"
            transform="grow-2"
            fixed-width
          />
        </li>
      </div>
    </b-sidebar>
  </div>
</template>

<script>
export default {
  name: "Favorites",
  props: {
    favoritesList: Array,
  },
  components: {},
  methods: {
    TextAbstract(text, length) {
      let last;
      if (text == null) {
        return "";
      }
      if (text.length <= length) {
        return text;
      }
      text = text.substring(0, length);
      last = text.lastIndexOf(" ");
      text = text.substring(0, last);
      return text + "...";
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.content {
  margin-left: auto;
  order: 2;
}

button {
  background-color: #1e3799;
  border: 0;
}

#sidebar-2 {
  margin-top: 64px;
  height: 100%;
}

.icon-spacing {
  margin: 0 0 0 4px;
}

.title-button {
  display: flex;
  justify-content: center;
  align-items: baseline;
}

ul,
li {
  list-style-type: none;
  text-align: left;
}

span {
  margin-left: 8px;
}

.poster-images {
  width: 100%;
  max-width: 44px !important;
  max-height: 66px !important;
}

.clear-button {
  margin-left: 30px;
  border-bottom: 5px solid #5352ed;
  background-color: #f1f2f6;
  color: #5352ed;
  border-radius: 0;
}

#shopping-button {
  margin-left: 5px;
  background-color: #f1f2f6;
  color: #212529;
}

.btn-primary:hover,
.btn-primary:focus,
.btn-primary:active,
.btn-primary:active:focus:not(:disabled):not(.disabled),
.btn:focus,
.btn:active,
.btn:hover {
  box-shadow: none !important;
  background-color: #57606f !important;
  outline: 0;
}
</style>
