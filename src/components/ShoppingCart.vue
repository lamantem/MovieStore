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
          <b-button @click="$emit('clearCheckoutList')" class="clear-button">Esvaziar</b-button>
        </div>
        <li v-for="item in shoppingCartList" :key="item.message">
          {{ item.title }}
          {{ item.poster_path }}
          R${{ item.cost }}
        </li>
        <b-button class="checkout-button" @click="toggleChecksdso()">Finalizar Compra</b-button>
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
      this.$emit('toggleCheckout', this.shoppingCartList);
    }
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

.clear-button {
  margin-left: 30px;
  border-bottom: 5px solid #5352ed;
  background-color: #f1f2f6;
  color: #5352ed;
  border-radius: 0;
}

.checkout-button{
  margin: 12px 0 0 0;
}
</style>
