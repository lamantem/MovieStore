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
        <p>Meu Carrinho</p>
        <li v-for="item in shoppingCartList" :key="item.message">
          {{ item.title }}
          {{ item.poster_path }}
          R${{ item.cost }}
        </li>
        <b-button @click="$emit('toggleCheckout')">AAAAAAAAAA</b-button>
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
  methods: {},
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
  height: 100%;
}

.icon-spacing {
  margin: 0 4px 0 0;
}
</style>
