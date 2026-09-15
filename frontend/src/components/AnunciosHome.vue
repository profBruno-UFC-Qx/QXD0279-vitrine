<template>
  <div class="mainDiv">
    <div class="header-anuncios">
      <h1 class="titulo">Anúncios Recentes</h1>
      
      <div class="filtros">
        <select class="select-filtro" v-model="filtroCategoria">
          <option value="" disabled selected hidden>Categoria</option>
          <option value="camisetas">Camisetas</option>
          <option value="calcas">Calças</option>
          <option value="calcados">Calçados</option>
        </select>

        <select class="select-filtro" v-model="filtroTamanho">
          <option value="" disabled selected hidden>Tamanho</option>
          <option value="p">P</option>
          <option value="m">M</option>
          <option value="g">G</option>
        </select>

        <select class="select-filtro" v-model="filtroPreco">
          <option value="" disabled selected hidden>Preço</option>
          <option value="menor">Menor Preço</option>
          <option value="maior">Maior Preço</option>
        </select>

        <select class="select-filtro" v-model="ordenarPor">
          <option value="" disabled selected hidden>Ordenar por</option>
          <option value="mais-recentes">Mais recentes</option>
          <option value="relevancia">Relevância</option>
        </select>
      </div>
    </div>

    <div class="anuncios">
      <AnuncioModal 
        v-for="anuncio in anuncios" 
        :key="anuncio.id" 
        :anuncio="anuncio" 
      />
    </div>
  </div>
</template>

<script>
import AnuncioModal from './AnuncioModal.vue';
import { anuncios } from '@/data/anuncios';

export default {
  name: 'AnunciosHome',
  components: {
    AnuncioModal
  },
  data() {
    return {
      filtroCategoria: '',
      filtroTamanho: '',
      filtroPreco: '',
      ordenarPor: '',
      anuncios
    }
  }
}
</script>

<style scoped>
.mainDiv {
  display: flex;
  flex-direction: column;
  min-height: 800px;
  padding: 20px;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  background-color: #f8fafc;
}

.header-anuncios {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 16px 0;
  margin-bottom: 20px;
}

.titulo {
  font-size: 28px;
  font-weight: 800;
  color: #0f172a;
  margin: 0;
}

.filtros {
  display: flex;
  gap: 12px;
  flex-wrap: wrap;
}

.select-filtro {
  padding: 8px 16px;
  border: 1px solid #cbd5e1;
  border-radius: 8px;
  background-color: #ffffff;
  color: #334155;
  font-size: 14px;
  font-weight: 500;
  cursor: pointer;
  outline: none;
  transition: border-color 0.2s;
}

.select-filtro:focus {
  border-color: #2563eb;
}

.anuncios {
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
  flex-wrap: wrap;
  gap: 10px;
}
</style>
