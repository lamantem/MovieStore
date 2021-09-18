<template>
  <div>
    <b-button v-b-toggle.sidebar-1>
      <font-awesome-icon
        class="navicon icon-spacing"
        :icon="['fas', 'heart']"
        transform="grow-6"
        fixed-width/>
    </b-button>
    <b-sidebar id="sidebar-1" title="Favoritos" shadow>
      <div class="px-3 py-2">
        <p>Favoritos</p>
      </div>
    </b-sidebar>
  </div>
</template>

<script>
export default {
  name: "ShoppingCart",
  components: {},
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
