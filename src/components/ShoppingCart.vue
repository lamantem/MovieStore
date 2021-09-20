<template>
  <div class="content">
    <b-button class="shadow-none" v-b-toggle.sidebar1-no-header>
      <font-awesome-icon
        class="navicon icon-spacing"
        :icon="['fas', 'shopping-cart']"
        transform="grow-6"
        fixed-width
      />
    </b-button>
    <b-sidebar
      id="sidebar1-no-header"
      title="Meu Carrinho"
      right
      no-header
      shadow
    >
      <div class="px-3 py-2">
        <div class="title-button">
          <p>Meu Carrinho</p>
          <b-button @click="$emit('clearCheckoutList')" class="clear-button"
            >Esvaziar</b-button
          >
        </div>
        <li v-for="item in shoppingCartList" :key="item.message">
          <img
            class="poster-images"
            :src="'http://image.tmdb.org/t/p/w500' + item.poster_path"
          />
          <span class="movie-title">`{{ TextAbstract(item.title, 11) }}</span>
          <span> 1 </span>
          <span>R${{ item.cost }}</span>
          <font-awesome-icon
            class="navicon icon-spacing sidebar-action-icon"
            :icon="['fas', 'trash']"
            transform="grow-2"
            fixed-width
          />
        </li>
        <b-button class="checkout-button" @click="toggleChecksdso()"
          >Finalizar Compra</b-button
        >
      </div>
    </b-sidebar>
  </div>
</template>

<script>
export default {
  name: "ShoppingCart",
  props: {
    shoppingCartList: Array,
  },
  components: {},
  methods: {
    toggleChecksdso() {
      this.$emit("toggleCheckout", this.shoppingCartList);
    },
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
  order: 2;
}

button {
  background-color: #1e3799;
  border: 0;
}

#sidebar-1 {
  margin-top: 64px;
  height: auto;
}

.icon-spacing {
  margin: 0 4px 0 0;
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

.movie-title {
  width: 5%;
}

span {
  margin-left: 8px;
}

.poster-images {
  width: 100%;
  max-width: 44px !important;
  max-height: 66px !important;
}

.sidebar-action-icon {
  margin-left: 8px;
}

.clear-button {
  margin-left: 30px;
  border-bottom: 5px solid #5352ed;
  background-color: #f1f2f6;
  color: #5352ed;
  border-radius: 0;
}

.checkout-button {
  margin: 12px 0 0 0;
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
