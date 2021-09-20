<template>
  <div class="outer">
    <div class="inner">
      <div class="col1"><h1 id="title">Finalizar Compra</h1></div>
      <div class="col2"></div>
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
        <ul>
          <li>
            <span class="image-header"> Imagem</span>
            <span class="cost-header"> Preço</span>
            <span class="quantity-header">Qtd</span>
            <span class="title-header">Nome</span>
          </li>
          <li v-for="item in shoppingCartList" :key="item.message">
            <span>
              <img
                class="poster-images"
                :src="'http://image.tmdb.org/t/p/w500' + item.poster_path"
            /></span>
            <span class="cost"> R${{ item.cost }}</span>
            <span class="quantity">1</span>
            <span class="quantity">{{ TextAbstract(item.title, 12) }}</span>
          </li>
        </ul>
      </div>

      <div class="col1"></div>
      <div class="col2">
        <li id="total-cost">
          <span class="image-header"> </span>
          <span class="cost-header">
            <h4>R$ {{ this.sumOfCosts() }}</h4></span
          >
          <span class="quantity-header"></span>
          <span class="title-header"> Total:</span>
        </li>
        <div>
          <b-button id="show-btn" @click="$bvModal.show('bv-modal-example')"
            >Open Modal</b-button
          >

          <b-modal id="bv-modal-example" hide-footer>
            <template #modal-title> Obrigado Maito Gai! </template>
            <div class="d-block text-center">
              <h3>Sua compra foi realizada com sucesso!</h3>
            </div>
            <b-button class="mt-3" block @click="backToStore()"
              >Ir para a loja
            </b-button>
          </b-modal>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Checkout",
  data() {
    return {
      totalCost: Float32Array,
    };
  },
  props: {
    shoppingCartList: Array,
  },
  components: {},
  beforeMount() {
    this.totalCost = 0;
  },
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
    backToStore() {
      this.$root.$bvModal.hide("bv-modal-example");
      this.$emit("backHome");
    },
    sumOfCosts() {
      this.totalCost = 0;
      if (this.shoppingCartList.length < 1) {
        return 0;
      }
      for (let i = 0; i < this.shoppingCartList.length; i++) {
        this.totalCost += this.shoppingCartList[i].cost;
        console.log(i);
      }
      return this.totalCost;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.outer {
  margin: 0;
  height: auto;
}

#title {
  padding: 16px 0 0 0;
}

ul,
li {
  list-style-type: none;
  padding: 4px 8px 4px 4px;
  text-align: left;
  width: 100%;
}

li {
  border-bottom: 1px solid black;
}

#total-cost {
  border-bottom: 0;
}

.quantity {
  margin: 20px 12px 0 0;
  float: right;
}

.cost {
  margin: 20px 12px 0 0;
  float: right;
}

.image-header {
  margin-left: -2px;
}

.cost-header,
.quantity-header {
  margin: 0 12px 0 0;
  float: right;
}

.title-header {
  margin: 0 48px 0 0;
  float: right;
}

.poster-images {
  margin: 0 4px;
  width: 100%;
  max-width: 44px !important;
  max-height: 66px !important;
}

.inner {
  padding-top: 75px;
  margin: 0 8px 8px 8px;
  height: auto;
  background-color: blueviolet;
  display: flex;
  flex-wrap: wrap;
}

.col1,
.col2 {
  flex: 1 1 800px;
  width: 50%;
  float: left;
}

.col1 {
  height: auto;
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
