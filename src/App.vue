<script setup>
import {ref} from "vue"

const items = ref([
    {
        id: 1,
        name: 'Camiseta',
        preco: 49.90
        
    },
    {
        id: 2,
        name: 'Calça',
        preco: 99.90
        
    },
    {
        id: 3,
        name: 'Meia',
        preco: 9.90
        
    },
    {
        id: 4,
        name: 'Sapato',
        preco: 199.90
        
    },
    {
        id: 5,
        name: 'Boné',
        preco: 29.90
    },
    {
        id: 6,
        name: 'Óculos',
        preco: 99.90
    },
    {
        id: 7,
        name: 'Relógio',
        preco: 299.90
    },
    {
        id: 8,
        name: 'Bermuda',
        preco: 79.90
    },
    {
        id: 9,
        name: 'Cueca',
        preco: 19.90
    },
    {
        id: 10,
        name: 'Meia',
        preco: 9.90
    }
])
</script>

<template>
  <ul>
    <li v-for="item in items" :key="item.id">
  <div id="quadro">
    <p id="titulo">{{ item.name }}</p>
    <p id="preco">R${{ item.preco }}</p>
    <p id="id">#{{ item.id  }}</p>
  </div>
    
    </li>
    
  </ul>
</template>

<style scoped>
#titulo {
  font-size: 18px;

}

#preco {

}

#quadro{
  border: solid 5px black;
  margin-bottom: 5px;
  
}




</style>
