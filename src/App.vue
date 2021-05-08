<template>
  <div class="cards">
    <b-nav>
      <p v-show="cartQt != 0">{{cartQt}} <b-icon icon="cart" class="h1 mb-2" shift-h="4" @click="openCart()" /></p>
      
    </b-nav>
    <b-container
      class="bv-example-row bv-example-row-flex-cols"
      id="app"
      fluid="sm"
    >
      <h1>Locadora de filmes</h1>
      <b-card-group columns>
        <b-row class="title">
          <b-col>
            <b-card
              v-for="filme in filmes"
              :key="filme.id"
              :img-src="filme.imagem"
              img-alt="Image"
              img-width="auto"
              img-height="auto"
            >
              <b-card-title>{{ filme.titulo }}</b-card-title>
              <b-card-text class="small text-muted"
                >Last updated 3 mins ago</b-card-text
              >
              <b-card-text>
                {{ filme.descricao }}
              </b-card-text>
              <b-card-text> R$ {{ filme.valor }},00 </b-card-text>
              <b-card-text>
                <b-icon
                  icon="star-fill"
                  variant="warning"
                  v-for="estrelas in filme.avaliacao"
                  :key="estrelas"
                ></b-icon>
                <b-icon
                  icon="star"
                  variant="warning"
                  v-for="estrelas_vazadas in 5 - filme.avaliacao"
                  :key="'star' + estrelas_vazadas"
                ></b-icon>
              </b-card-text>
              <b-button
                v-if="filme.estoqueDisponivel > 1"
                @click="addToCart(filme)"
                >ALUGAR</b-button
              >
              <b-button
                v-else-if="filme.estoqueDisponivel == 1"
                @click="addToCart(filme)"
                >ÚLTIMO DISPNÍVEL</b-button
              >
              <b-button v-else>INDISPONÍVEL</b-button>
            </b-card>
          </b-col>
        </b-row>
      </b-card-group>
    </b-container>
  </div>
</template>

<script>
import "bootstrap/dist/css/bootstrap.css";
import "bootstrap-vue/dist/bootstrap-vue.css";

export default {
  name: "App",
  data() {
    return {
      cart: Array(),
      hora: new Date(),
      filmes: [
        {
          id: 1,
          estoqueDisponivel: 3,
          titulo: "Hulk",
          descricao: "Filme Ruim",
          valor: 2,
          avaliacao: 1,
          imagem: "https://i.imgur.com/0uthCmp.jpg",
        },
        {
          id: 2,
          estoqueDisponivel: 2,
          titulo: "Homem de Ferro",
          descricao: "Homem de Ferro",
          valor: 10,
          avaliacao: 3,
          imagem: "https://i.imgur.com/OA8pDFM.jpg",
        },
        {
          id: 3,
          estoqueDisponivel: 4,
          titulo: "Thor",
          descricao: "Bonito ",
          valor: 20,
          avaliacao: 3,
          imagem: "https://i.imgur.com/mt4ZRzw.jpg",
        },
        {
          id: 4,
          estoqueDisponivel: 2,
          titulo: "Capitão América",
          descricao: "Um filme de capitão",
          valor: 40,
          avaliacao: 3,
          imagem: "https://i.imgur.com/UFmSVtZ.jpg",
        },
        {
          id: 5,
          estoqueDisponivel: 9,
          titulo: "Doutor Estranho",
          descricao: "Magia",
          valor: 10,
          avaliacao: 4,
          imagem: "https://i.imgur.com/pVEDruM.jpg",
        },
        {
          id: 6,
          estoqueDisponivel: 1,
          titulo: "Pantera Negra",
          descricao: "Um segundo filme de força",
          valor: 10,
          avaliacao: 5,
          imagem: "https://i.imgur.com/JOSEGKf.jpg",
        },
      ],
    };
  },
  methods: {
    addToCart: function (filme) {
      let myCart = this.cart;
      let filmIndx = myCart.findIndex((obj) => obj.id == filme.id);
      if (filmIndx == -1) {
        myCart.push(filme);
        this.$emit("update:cart", myCart);
      }
    },
  },
  computed: {
    cartQt: function () {
      return this.cart.length;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
