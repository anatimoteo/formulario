<script setup>
import { reactive, ref } from 'vue'
const titulo = ref('Oi VueJs!')
const mostrarResultado = ref(false)
const produto = reactive({
  nome: '',
  preco: 0,
  quantidade: 0,
  categorias: []
})

const categorias = [
  {
    id: 1,
    nome: 'Eletrônicos'
  },

  {
    id: 2,
    nome: 'Vestuário'
  },

  {
    id: 3,
    nome: 'Brinquedos'
  },

  {
    id: 4,
    nome: 'Móveis'
  },

]
function formatarPreco(preco) {
  return `R$ ${preco.toFixed(2).replace('.', ',')}`
}
</script>

<template>
  <h1>{{ titulo }}</h1>
  <div class="container">
    <div class="formulario">
      <h2>formulário</h2>
      <input type="text" v-model="titulo" />
      <h3>Informar dados do produto</h3>
      <div class="row">
        <label for="">Nome:</label>
        <input type="text" v-model="produto.nome" />
      </div>

      <div class="row">
        <label for=""> Preço (em reais): </label>
        <input type="number" step="0.01" v-model="produto.preco" />
      </div>

      <div class="row">
        <label for=""> Quantidade: </label>
        <input type="text" v-model="produto.quantidade" />
      </div>

      <fieldset>
        <legend>Categorias</legend>
        <div class="itens-checkbox">
          <template v-for="categoria in categorias" :key="categoria.id">
            <input type="checkbox" :value="categoria.id" v-model="produto.categorias" /> {{ categoria.nome }}
          </template>
        </div>
      </fieldset>

      <button @click="mostrarResultado = !mostrarResultado">Mostrar</button>
    </div>

    <div class="resultado">
      <div v-if="mostrarResultado" class="resultado">
        <h2>Dados do produto</h2>
        <p>Nome: {{ produto.nome }}</p>
        <P>Preço: {{ formatarPreco(produto.preco) }}</P>
        <p>Em estoque: {{ produto.quantidade }}</p>
        <p>Categorias: {{ produto.categorias }}</p>
        <p>{{ mostrarResultado }}</p>
      </div>
    </div>
  </div>
</template>

<style scoped>
.formulario {
  background-color: rgb(240, 208, 255);
}

.resultado {
  background-color: rgb(238, 204, 253);
}

.container {
  display: flex;
  gap: 2rem;
  justify-content: center;
  margin-top: 1rem;
}

.formulario,
.resultado {
  width: 45vw;
  min-height: 70vh;
  border-radius: 20px;
  padding: 20px;
}

.formulario .row {
  margin: 1.3rem 0;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  width: 80%;
}

.formulario .itens-checkbox {
  display: grid;
  grid-template-columns: auto 1fr;
  align-items: center;
}

fieldset {
  border: hidden;
}
</style>