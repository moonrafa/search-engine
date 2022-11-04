<script setup>
import { ref } from "vue";
let input = ref("");
const results = [];
function filteredList() {
  return results.filter((result) =>
    result.toLowerCase().includes(input.value.toLowerCase())
  );
}</script>

<template>
  <div class="flex">
  <input type="text" v-model="input" placeholder="Pesquisar..." />
  <div class="item tabela" v-for="result in filteredList()" :key="result">
    <p>{{ result }}</p>
  </div>
  <div class="item error" v-if="input && !filteredList().length">
    <p>Não há resultados. Tente outra palavra! </p>
  </div>
</div>
</template>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Montserrat&display=swap");
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  font-family: "Montserrat", sans-serif;
}

body {
  min-height: 100vh;
}

input {
  display: block;
  width: 350px;
  margin: 20px auto;
  padding: 10px 45px;
  background: white url("assets/search-icon.svg") no-repeat 15px center;
  background-size: 15px 15px;
  font-size: 16px;
  border: none;
  border-radius: 5px;
  box-shadow: rgba(50, 50, 93, 0.25) 0px 2px 5px -1px,
    rgba(0, 0, 0, 0.3) 0px 1px 3px -1px;
}
.flex {
  display: flex;
  flex-direction: column;
  margin: 0 auto;
}

.item {
  width: 350px;
  margin: 0 auto 10px auto;
  padding: 10px 20px;
  color: white;
  border-radius: 5px;
  box-shadow: rgba(0, 0, 0, 0.1) 0px 1px 3px 0px,
    rgba(0, 0, 0, 0.06) 0px 1px 2px 0px;
}

.tabela {
  background-color: #41B883;
  cursor: pointer;
}

.error {
  background-color: tomato;
}
</style>
