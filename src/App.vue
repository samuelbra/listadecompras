<template>
  <h1>{{ titulo }}</h1>

  <input
    v-model="produto.descricao"
    type="text"
    placeholder="Descrição do Produto"
  />

  <app-btn @click="adicionarProduto">Adicionar</app-btn>

  <table border="1">
    <thead>
      <th>Concluída</th>

      <th>Descrição</th>
    </thead>
    <tbody>
      <tr
        v-for="iterador in produtos"
        :key="iterador"
        :class="{ riscado: iterador.concluida }"
      >
        <td>
          <input type="checkbox" v-model="iterador.concluida" />
        </td>
        <td>{{ iterador.descricao }}</td>
      </tr>
    </tbody>
  </table>
</template>

<script setup>
import AppBtn from "./components/AppBtn.vue";
import { reactive, ref } from "vue";

// Composition API
const titulo = ref("Lista de Compras");
const produtos = reactive([]);
const produto = reactive({
  descricao: "",
  concluida: false,
});

function adicionarProduto() {
  produtos.push(Object.assign({}, produto));
}
</script>

<style>
.riscado {
  text-decoration: line-through;
}
</style>
