<script setup>
import { ref } from 'vue'

const produtos = ref([
  {
    id: 1,
    nome: 'Computador',
    quantidade: 0,
    preco: 2500.90
  },
  {
    id: 2,
    nome: 'Notebook Gamer',
    quantidade: 0,
    preco: 8399.99
  },
  {
    id: 3,
    nome: 'Celular',
    quantidade: 0,
    preco: 1800
  },
  {
    id: 4,
    nome: 'Ipad',
    quantidade: 0,
    preco: 6999.99
  },
  {
    id: 5,
    nome: 'Tablet',
    quantidade: 0,
    preco: 1280.9
  },
  {
    id: 6,
    nome: 'Xbox Series X',
    quantidade: 0,
    preco: 5999.9
  },
  {
    id: 7,
    nome: 'Playstation 5',
    quantidade: 0,
    preco: 4420.9
  },
  {
    id: 8,
    nome: 'Nintendo Switch',
    quantidade: 0,
    preco: 2299.9
  },
  {
    id: 9,
    nome: 'Nintendo 69',
    quantidade: 0,
    preco: 6969.69
  },
  {
    id: 10,
    nome: 'Quest 5',
    quantidade: 0,
    preco: 9999.99
  },
  {
    id: 11,
    nome: 'Playstation 2',
    quantidade: 0,
    preco: 199.9
  },

  {
    id: 12,
    nome: 'Mega drive',
    quantidade: 0,
    preco: 399.9
  }
])

const carrinhoCria = ref({
  items: [],
  total: 0
})

let valorTotal = ref(0)

function addCarrinho(recursos) {
  carrinhoCria.value.items.push({
    id: recursos.id,
    nome: recursos.nome,
    preco: recursos.preco,
    quantidade: recursos.quantidade,
    total: recursos.preco * recursos.quantidade
  });
  carrinhoCria.value.total += recursos.preco * recursos.quantidade
}

function mais(index) {
  produtos.value[index].quantidade++
  const pos = carrinhoCria.value.items.indexOf(carrinhoCria.value.items.find(c => c.id === produtos.value[index].id))
  if (pos != -1) {
    carrinhoCria.value.total -= carrinhoCria.value.items[pos].total
    carrinhoCria.value.items[pos].total = ++carrinhoCria.value.items[pos].quantidade * carrinhoCria.value.items[pos].preco
    carrinhoCria.value.total += carrinhoCria.value.items[pos].total

  }
}

function menos(index) {
  produtos.value[index].quantidade--
  const pos = carrinhoCria.value.items.indexOf(carrinhoCria.value.items.find(c => c.id === produtos.value[index].id))


  if (pos != +1) {
    carrinhoCria.value.total -= carrinhoCria.value.items[pos].total
    carrinhoCria.value.items[pos].total = --carrinhoCria.value.items[pos].quantidade * carrinhoCria.value.items[pos].preco
    carrinhoCria.value.total += carrinhoCria.value.items[pos].total
  }
}

function limparGamer(){
carrinhoCria.value.items = []
carrinhoCria.value.total = 0
}

</script>

<template>    
    <div class="modal fade" id="exampleModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
      <div class="modal-dialog modal-dialog-centered">
        <div class="modal-content">
          <div class="modal-header">
            <p class="modal-title fs-5" id="exampleModalLabel">Produtos:</p>
            <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
          </div>
          <div class="modal-body">
            <div v-for="(carrinhoItem, index) in carrinhoCria.items" :key="index">              
              <strong> {{ carrinhoItem.id }} - {{ carrinhoItem.nome }}</strong>
              <hr>
              <p>Preço BRL: {{ carrinhoItem.preco }} </p> 
              <p>Quantidade: {{ carrinhoItem.quantidade }} </p>
              <p>Preço: {{ carrinhoItem.total }}</p>
            </div>
            
            <p v-if="carrinhoCria.items.length > 0">Total: {{ carrinhoCria.total }} BRL</p>
            <p v-else>Nenhum Item</p>
          </div>
          <div class="modal-footer">
            <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Sair</button>
            <button @click="limparGamer" type="button" class="btn btn-warning">Limpar</button>
          </div>
        </div>
      </div>
    </div>

    <nav class="navbar navbar-light bg-primary">
  <div class="container-fluid">
    <a class="navbar-brand">💻 Bryan's Store</a>
    <form class="d-flex">
      <input class="form-control me-2" type="Procurar" placeholder="Procurar" aria-label="Procurar">
      <button class="btn btn-outline-success" type="submit">Procurar</button>
    </form>
  </div>
</nav>
  <div class="container">
    <button type="button" class="btn btn-primary p-3 mt-2 navbar " data-bs-toggle="modal" data-bs-target="#exampleModal">
      🛒 Carrinho
    </button>
    <div class="row">
      <div v-for="(recursos, index) in produtos" :key="recursos.id" class="tema col-3">
        <h1>{{ recursos.id }} - {{ recursos.nome }}</h1>
        <br />
        <h6>Preço: {{ recursos.preco }} R$</h6>
        <h6>Quantidade: {{ recursos.quantidade }}</h6>

        <button type="button" @click="menos(index)" class="button">-</button>
        <button type="button" @click="addCarrinho(recursos)" class="button">Add</button>
        <button type="button" @click="mais(index)" class="button">+</button>
      </div>
    </div>
  </div>
  <div class="barra">
    <h1>Melhores aparelhos</h1>
  </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Bruno+Ace+SC&display=swap');
.navbar-brand {
  color: #fff;
  font-size: 28px;
  font-weight: bold;
  margin-left: 20px;
}

/* Estilo para a barra de navegação */
.navbar {
  background-color: #077bff;
  
}

/* Estilo para o formulário de pesquisa */
.form-control {
  width: 200px;
  margin-right: 10px;
}

/* Estilo para o botão de pesquisa */
.btn-outline-success {
  color: #fff;
  border-color: #fff;
  margin-right: 20px;
}

/* Estilo para o título "Melhores aparelhos" */
.barra h1 {
  color: #fff;
  font-size: 36px;
  font-weight: bold;
  margin-top: 50px;
  
}

/* Estilo para a div dos produtos */
.container {
  margin-top: 50px;
}

/* Estilo para os cards dos produtos */
.tema {
  background-color: #f8f9fa;
  margin: 10px;
  padding: 10px;
  border-radius: 5px;
  text-align: center;
  box-shadow: 0px 0px 5px rgba(0, 0, 0, 0.1);
}

/* Estilo para os botões de adicionar/remover do carrinho */
.button {
  background-color: #077bff;
  color: #fff;
  border: none;
  border-radius: 5px;
  padding: 5px 10px;
  margin: 5px;
  font-weight: bold;
  cursor: pointer;
}

/* Estilo para o modal do carrinho */
.modal-content {
  border-radius: 5px;
}

/* Estilo para o título do modal do carrinho */
.modal-title {
  font-weight: bold;
}

/* Estilo para o botão de fechar o modal */
.btn-close {
  color: #000;
}

/* Estilo para o botão de limpar o carrinho */
.btn-warning {
  color: #fff;
  background-color: #077bff;
  border-color: #077bff;
  font-weight: bold;
}

/* Estilo para o texto "Nenhum Item" do modal do carrinho */
.modal-body p:last-child {
  font-style: italic;
}


</style>