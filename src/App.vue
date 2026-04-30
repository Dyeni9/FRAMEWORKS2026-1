<script setup>
import { ref } from 'vue'

const novoItem = ref('')
const cesta = ref([])
 
const adicionarProduto = () => {
  if (novoItem.value.trim() !== '') {
    cesta.value.push({
      id: Date.now(),
      nome: novoItem.value
    })
    novoItem.value = ''
  }
}
</script>

<template>
  <div class="container">
    <h1>Gerenciador de Compras</h1>

    <input 
      v-model="novoItem" 
      @keyup.enter="adicionarProduto" 
      placeholder="Digite o produto..."
    >
    <button @click="adicionarProduto">Adicionar</button>

    <ul>
      <li v-for="item in cesta" :key="item.id">
        {{ item.nome }}
      </li>
    </ul>
  </div>
</template>