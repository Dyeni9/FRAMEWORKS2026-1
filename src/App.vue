<script setup>
import { ref } from 'vue'

const novoItem = ref('')
const cesta = ref([])
</script>

<template>
  <div class="container">
    <h1>Gerenciador de Compras</h1>

    <input 
      v-model="novoItem" 
      placeholder="Digite o produto..."
    >
    <button>Adicionar</button>
  </div>
</template>

<style scoped>
.container { font-family: sans-serif; max-width: 400px; margin: 20px auto; }
</style>