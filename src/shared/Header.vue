<template>
  <div class="header">
    <div id="column1">
      <a href="#">
        <font-awesome-icon
          class="logo icon-spacing"
          :icon="['fas', 'film']"
          transform="grow-6"
          fixed-width/>
      </a>
    </div>

    <div id="column2">
      <input class="search-field" type="text" placeholder="Search title.." />
    </div>

    <div id="column3">
      <ShoppingCart></ShoppingCart>
      <Favorites></Favorites>
    </div>
  </div>
</template>

<script>
import ShoppingCart from "../components/ShoppingCart.vue";
import Favorites from "../components/Favorites.vue";

export default {
  name: "Header",
  components: {
    ShoppingCart,
    Favorites,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.header {
  padding: 14px;
  background-color: #7fe4d5;
  overflow: hidden;
  display: flex;
}

.header > div {
  flex-grow: 1;
}

#column1,
#column3 {
  width: 25%;
  display: inline-block;
}

#column2 {
  width: 50%;
  display: inline-block;
}

.search-field {
  width: 100%;
}

.logo {
  float: left;
}

.navicon {
  float: right;
}

.icon-spacing {
  margin: 0 8px 0 8px;
}
</style>
