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
          <b-button @click="$emit('clearFavoritesList')" class="clear-button">Esvaziar</b-button>
        </div>
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

.title-button {
  display: flex;
  justify-content: center;
  align-items: baseline;
}

.clear-button {
  margin-left: 30px;
  border-bottom: 5px solid #5352ed;
  background-color: #f1f2f6;
  color: #5352ed;
  border-radius: 0;
}
</style>
