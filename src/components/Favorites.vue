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
        <p>Meus Favoritos</p>
        <li v-for="item in favoritesList" :key="item.message">
          {{ item.title }}
          {{ item.poster_path }}
          R${{ item.cost }}
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
</style>
