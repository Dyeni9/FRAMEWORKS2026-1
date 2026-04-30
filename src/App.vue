<script setup>
import { ref } from 'vue'

const novoItem = ref('')
const cesta = ref([])

const adicionarProduto = () => {
  if (novoItem.value.trim() !== '') {
    cesta.value.push({ id: Date.now(), nome: novoItem.value })
    novoItem.value = ''
  }
}

const removerProduto = (id) => {
  cesta.value = cesta.value.filter(item => item.id !== id)
}
</script>

<template>
  <div class="container">
    <h1>Gerenciador de Compras</h1>

    <input v-model="novoItem" @keyup.enter="adicionarProduto" placeholder="Digite o produto...">
    <button @click="adicionarProduto">Adicionar</button>

    <p>Total de itens: <strong>{{ cesta.length }}</strong></p>

    <div v-if="cesta.length > 0">
      <h2>Minha Cesta de Compras</h2>
      <ul>
        <li v-for="item in cesta" :key="item.id">
          {{ item.nome }}
          <button @click="removerProduto(item.id)">Remover</button>
        </li>
      </ul>
    </div>

    <p v-else>Sua cesta está vazia! Adicione produtos para começar.</p>
  </div>
</template>

<style scoped>
.container { font-family: sans-serif; max-width: 400px; margin: 20px auto; }
li { margin-bottom: 8px; display: flex; justify-content: space-between; }
</style>