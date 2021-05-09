<template>
  <div class="cards">
    <nav>
      <ul class="menuItems">
        <li>
          <a id="title" href="#" data-item="Home"
            ><b-icon icon="diamond-half" class="h3 mb-2" />SGI</a
          >
        </li>
        <li>
          <input
            type="text"
            class="form-control"
            name="x"
            id="search"
            placeholder="Search"
          />
          <span class="input-group-btn">
            <button class="btn btn-default" type="button">
              <span><b-icon icon="search" class="h1 md-2"></b-icon></span>
            </button>
          </span>
        </li>
        <li><a href="#" data-item="Login">Login
          <span>
        <b-icon icon="person-circle" class="h2 md-2"/>
        </span>
        </a>
        
        </li>
      </ul>
    </nav>
    
    <table>
<tr id="header">
      <th>
        <p>
          Recomendações
        </p>
      </th>
</tr>

      <tr>
        <td>
          <b-card v-for="filme in filmes"
          :key="filme.id"
          :img-src="filme.imagem"
          img-width="190px"
          img-height="120px">
           <b-card-title>{{ filme.titulo }}</b-card-title>
           <b-card-text>
                {{ filme.descricao }}
              </b-card-text>
             
          </b-card>
        </td>
      </tr>

    </table>

    <table>
<tr id="header">
      <th>
        <p>
          Shows
        </p>
      </th>
</tr>

      <tr>
        <td>
          <b-card v-for="evento in shows"
          :key="evento.id"
          :img-src="evento.imagem"
          img-height="120px"
          img-width="190px">
           <b-card-title>{{ evento.titulo }}</b-card-title>
           <b-card-text>
                {{ evento.descricao }}
              </b-card-text>
             
          </b-card>
        </td>
      </tr>

    </table>

    <table>
<tr id="header">
      <th>
        <p>
          Eventos
        </p>
      </th>
</tr>

      <tr>
        <td>
          <b-card v-for="evento in eventos"
          :key="evento.id"
          :img-src="evento.imagem"
          img-height="120px">
           <b-card-title>{{ evento.titulo }}</b-card-title>
           <b-card-text>
                {{ evento.descricao }}
              </b-card-text>
             
          </b-card>
        </td>
      </tr>

    </table>
      
      
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
      shows: [
        {
          id: 1,
          estoqueDisponivel: 3,
          titulo: "Rolling Stones",
          descricao: "Show do Rolling Stones",
          valor: 2,
          avaliacao: 1,
          imagem: "https://i.imgur.com/rxTpPqz.jpg",
        },
        {
          id: 2,
          estoqueDisponivel: 2,
          titulo: "Roger Waters",
          descricao: "Show Roger Waters",
          valor: 10,
          avaliacao: 3,
          imagem: "https://imgur.com/VwnDMwX.jpg",
        },
        {
          id: 3,
          estoqueDisponivel: 4,
          titulo: "Lollapalooza 2021",
          descricao: "Dezenas de atrações",
          valor: 20,
          avaliacao: 3,
          imagem: "https://i.imgur.com/d7uHXqV.jpg",
        },
        {
          id: 4,
          estoqueDisponivel: 2,
          titulo: "Skank",
          descricao: "Show do Skank",
          valor: 40,
          avaliacao: 3,
          imagem: "https://i.imgur.com/pYNp5JH.jpg",
        },
        {
          id: 5,
          estoqueDisponivel: 9,
          titulo: "Ivete Sangalo",
          descricao: "Show da Ivete Sangalo",
          valor: 10,
          avaliacao: 4,
          imagem: "https://i.imgur.com/MZeepdZ.jpg",
        },
        {
          id: 6,
          estoqueDisponivel: 1,
          titulo: "Gilberto Gil",
          descricao: "Show do Gilberto Gil",
          valor: 10,
          avaliacao: 5,
          imagem: "https://i.imgur.com/iJTVfso.jpg",
        },
      ],
      eventos: [
        {
          id: 1,
          estoqueDisponivel: 3,
          titulo: "Maratona de Copacabana",
          descricao: "Corrida",
          valor: 2,
          avaliacao: 1,
          imagem: "https://i.imgur.com/Xt5XJOS.jpg",
        },
        {
          id: 2,
          estoqueDisponivel: 2,
          titulo: "Samba da Pedra do Sal",
          descricao: "Evento popular",
          valor: 10,
          avaliacao: 3,
          imagem: "https://i.imgur.com/Djg6lTm.jpg",
        },
        {
          id: 3,
          estoqueDisponivel: 4,
          titulo: "Iron Man",
          descricao: "Corrida de resistência",
          valor: 20,
          avaliacao: 3,
          imagem: "https://i.imgur.com/r55R957.png",
        },
        {
          id: 4,
          estoqueDisponivel: 2,
          titulo: "Escalada Pedra da Gávea",
          descricao: "Programa ao ar livre",
          valor: 40,
          avaliacao: 3,
          imagem: "https://i.imgur.com/GvtDKaE.jpg",
        },
        {
          id: 5,
          estoqueDisponivel: 9,
          titulo: "Canoa havaiana",
          descricao: "Remada até as ilhas cagarras",
          valor: 10,
          avaliacao: 4,
          imagem: "https://i.imgur.com/Q1CocuB.jpg",
        },
        {
          id: 6,
          estoqueDisponivel: 1,
          titulo: "Pescaria na baia de guanabara",
          descricao: "Pescaria",
          valor: 10,
          avaliacao: 5,
          imagem: "https://i.imgur.com/MwBHUwK.jpg",
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
.cards {
  background-color: black;
  color: white;
}
nav {
  height: 120px;
  width: 100%;
  background: #f9f9f9;
  display: flex;
  justify-content: space-around;
  align-items:center;
}
nav .menuItems {
  margin: 20px;
  padding: 10px;
  list-style:none;
  display: flex;
  justify-content: space-around;
  align-items: stretch;
}

nav li {
  margin: 50px;
  display: inline-flex;
  flex-direction: row;
  float: left;
}
nav a {
  text-decoration: none;
  color: #8f8f8f;
  font-size: 24px;
  font-weight: 400;
  transition: all 0.5s ease-in-out;
  position: relative;
  text-transform: uppercase;
  float: left;
  padding: 12px;
}
table{
  height: fit-content;
  width: 100%;
  display: table;
  overflow: hidden;
  justify-content: space-around;
  border-color: white;
  border-style: groove;
  border-width: 3px;
  margin-bottom: 3px;
  margin-top: 5px;
}
th{
  top: 20px;
  display: flex;
  justify-content: space-around;
  text-align: center;
}
#header{
  height: 45px;
  background-color: #1d2022;
}
td{
  display: flex;
  flex-direction: row;
  align-content: center;
  justify-content: space-around;
  align-items: stretch;
  background-color: #282929;
}
.card{

  display: flex;
  object-fit: cover;
  min-width: 120px;
  align-items: center;
  margin: 2px;
  background-color: #111416;

}
.card img{
  height: 120px;
  width: 100%;
  max-width: 188px;
}
</style>
