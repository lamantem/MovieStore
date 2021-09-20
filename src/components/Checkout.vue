<template>
  <div class="outer">
    <h1 id="title">Finalizar Compra</h1>
    <div class="inner">
      <div class="col1">
        <input
          class="input large-input"
          type="text"
          placeholder="Nome Completo"
        />
        <div>
          <input class="input small-input" type="text" placeholder="CPF" />
          <input class="input small-input" type="text" placeholder="Celular" />
        </div>
        <input class="input large-input" type="text" placeholder="E-mail" />
        <div>
          <input class="input small-input" type="text" placeholder="CEP" />
          <input class="input small-input" type="text" placeholder="Endereço" />
        </div>
        <div>
          <input class="input small-input" type="text" placeholder="Cidade" />
          <input class="input small-input" type="text" placeholder="Estado" />
        </div>
      </div>

      <div class="col2">
        <li v-for="item in shoppingCartList" :key="item.message">
          <img
            class="poster-images"
            :src="'http://image.tmdb.org/t/p/w500' + item.poster_path"
          />
          {{ item.title }}
          R${{ item.cost }}
        </li>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Checkout",
  data() {
    return {
      itemsCheckout: [{ message: "ooooo" }, { message: "zaaaaa" }],
    };
  },
  props: {
    shoppingCartList: Array,
  },
  components: {},
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.outer {
  margin: 0;
  height: auto;
  background-color: grey;
}

#title {
  padding: 16px 0 0 0;
}

ul,
li {
  list-style-type: none;
  text-align: left;
}

.poster-images {
  width: 100%;
  max-width: 44px !important;
  max-height: 66px !important;
}

.inner {
  margin: 16px 8px 8px 8px;
  height: auto;
  background-color: blueviolet;
  display: flex;
  flex-wrap: wrap;
}

.col1,
.col2 {
  flex: 1 1 350px;
  width: 50%;
  float: left;
}

.col1 {
  height: auto;
  margin: 16px 0;
  background-color: yellow;
}

.large-input {
  width: 80%;
  margin: 4px 0;
}

.small-input {
  width: 40%;
  margin: 4px 0;
}

.col2 {
  height: auto;
  background-color: greenyellow;
}

.purchase-list {
  margin-top: 10px;
}

#finish {
  margin-top: 85px;
  height: 35px;
  width: 240px;
}
</style>
