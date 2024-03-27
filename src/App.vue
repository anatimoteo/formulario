<script setup>
import { reactive, ref } from 'vue'

const titulo = ref('VueJs')
const mostrarResultado = ref(false)
const produto = reactive({
  nome: '',
  preco: 0,
  qntd: 0,
  categorias: []
})
</script>

<template>
  <h1> {{ titulo }}</h1>
  <div class="container">

    <div class="formulario">

      <h2>Formulário</h2>
      <input type="text" v-model="titulo" />
      <h3>Informar dados do produto</h3>
      <div class="row">
        <label for="">Nome:</label>
        <input type="text" v-model="produto.nome" />
        <input type="text" />
        <div class="row">
          <label for="">Preço:</label>
          <input type="text" />
        </div>
        <div class="row">
          <label for="">Quantidade:</label>
          <input type="text" />
        </div>
        <button @click="mostrarResultado = !mostrarResultado">Mostrar</button>
      </div>
    </div>
    <div v-if="mostrarResultado" class="resultado">
      <h2>Dados do produto</h2>
      <p>Nome: {{ produto.nome }}</p>
      <p>Preço: {{ produto.preco }}</p>
      <p>Em estoque: {{ produto.qntd }}</p>
      <p>Categorias: {{ produto.categorias }}</p>
      <p>{{ mostrarResultado }}</p>
    </div>
  </div>
</template>


<style scoped>
.container {
  display: flex;
  gap: 2rem;
  justify-content: center;
  margin-top: 1rem;
}

.formulario {
  background-color: rgb(222, 164, 255);
}

.formulario .row {
  width: 80%;
  margin: 1.3rem 0;
  display: flex;
  justify-content: space-between;
}

.resultado {
  background-color: rgb(167, 129, 255);
}

.formulario,
.resultado {
  width: 45vw;
  min-height: 70vh;
  border-radius: 20px;
  padding: 20px;
}
</style>
