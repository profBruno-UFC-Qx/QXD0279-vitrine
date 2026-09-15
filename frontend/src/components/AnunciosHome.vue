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
        v-for="(anuncio, index) in anuncios" 
        :key="index" 
        :anuncio="anuncio" 
      />
    </div>
  </div>
</template>

<script>
import AnuncioModal from './AnuncioModal.vue';

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
      anuncios: [
        {
          "nomeDoItem": "Camiseta Básica Preta",
          "descricao": "Camiseta masculina preta, 100% algodão, tamanho M.",
          "endereco": "Rua das Flores, 120 - Centro",
          "preco": 39.90
        },
        {
          "nomeDoItem": "Calça Jeans Azul",
          "descricao": "Calça jeans azul tradicional, corte slim, tamanho 42.",
          "endereco": "Av. Santos Dumont, 850 - Aldeota",
          "preco": 119.90
        },
        {
          "nomeDoItem": "Moletom Cinza",
          "descricao": "Moletom cinza com capuz, confortável para dias frios, tamanho G.",
          "endereco": "Rua José Vilar, 430 - Meireles",
          "preco": 89.90
        },
        {
          "nomeDoItem": "Camisa Social Branca",
          "descricao": "Camisa social branca de manga longa, tamanho M.",
          "endereco": "Av. Beira Mar, 1500 - Meireles",
          "preco": 99.90
        },
        {
          "nomeDoItem": "Bermuda Jeans",
          "descricao": "Bermuda jeans azul clara, modelo casual, tamanho 40.",
          "endereco": "Rua Monsenhor Tabosa, 320 - Centro",
          "preco": 69.90
        },
        {
          "nomeDoItem": "Jaqueta Corta-Vento",
          "descricao": "Jaqueta corta-vento leve, ideal para atividades ao ar livre, tamanho G.",
          "endereco": "Av. Washington Soares, 2100 - Edson Queiroz",
          "preco": 129.90
        },
        {
          "nomeDoItem": "Vestido Floral",
          "descricao": "Vestido estampado com flores, tecido leve e confortável, tamanho M.",
          "endereco": "Rua Dom Luís, 700 - Aldeota",
          "preco": 109.90
        },
        {
          "nomeDoItem": "Tênis Casual Branco",
          "descricao": "Tênis casual branco de uso diário, tamanho 41.",
          "endereco": "Av. Bezerra de Menezes, 950 - Fátima",
          "preco": 149.90
        }
      ]
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