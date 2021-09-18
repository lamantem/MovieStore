<template>
  <div>
    <b-button v-b-toggle.sidebar-2>
      <font-awesome-icon
        class="navicon icon-spacing"
        :icon="['fas', 'shopping-cart']"
        transform="grow-6"
        fixed-width/>
    </b-button>
    <b-sidebar id="sidebar-2" title="Carrinho" shadow>
      <div class="px-3 py-2">
        <p>Carrinho</p>
      </div>
    </b-sidebar>
  </div>
</template>

<script>
export default {
  name: "Favorites",
  components: {},
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
