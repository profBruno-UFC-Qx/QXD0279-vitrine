<template>
  <div class="card-anuncio">
    <div class="imagem-container">
      <div class="imagem-placeholder" aria-hidden="true">
        <svg width="64" height="64" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round">
          <path d="M6 2 3 6v14a2 2 0 0 0 2 2h14a2 2 0 0 0 2-2V6l-3-4z"></path>
          <path d="M3 6h18"></path>
          <path d="M16 10a4 4 0 0 1-8 0"></path>
        </svg>
      </div>
      <button class="btn-favorito" aria-label="Favoritar">
        <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="#666" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
          <path d="M20.84 4.61a5.5 5.5 0 0 0-7.78 0L12 5.67l-1.06-1.06a5.5 5.5 0 0 0-7.78 7.78l1.06 1.06L12 21.23l8.78-8.78 1.06-1.06a5.5 5.5 0 0 0 0-7.78z"></path>
        </svg>
      </button>
    </div>

    <div class="conteudo">
      <div class="cabecalho">
        <h3 class="titulo">{{ anuncio.nomeDoItem }}</h3>
        <span class="preco">{{ precoFormatado }}</span>
      </div>

      <p class="descricao">{{ anuncio.descricao }}</p>

      <div class="localizacao">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="#666" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
          <path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0 1 18 0z"></path>
          <circle cx="12" cy="10" r="3"></circle>
        </svg>
        <span>{{ anuncio.endereco }}</span>
      </div>

      <RouterLink
        class="btn-anuncio"
        :to="{ name: 'detalhes-anuncio', params: { id: anuncio.id } }"
      >
        Ver anúncio
      </RouterLink>
    </div>
  </div>
</template>

<script>
export default {
  name: "AnuncioModal",
  props: {
    anuncio: {
      type: Object,
      required: true
    }
  },
  computed: {
    precoFormatado() {
      return new Intl.NumberFormat("pt-BR", {
        style: "currency",
        currency: "BRL"
      }).format(this.anuncio.preco)
    }
  }
}
</script>

<style scoped>
.card-anuncio {
  width: 340px;
  border: 1px solid #e2e8f0;
  border-radius: 12px;
  overflow: hidden;
  background-color: #ffffff;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.05);
  margin: 2px;
}

.imagem-container {
  position: relative;
  width: 100%;
  height: 260px;
}

.imagem-placeholder {
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #94a3b8;
  background: linear-gradient(135deg, #f1f5f9, #e2e8f0);
}

.btn-favorito {
  position: absolute;
  top: 12px;
  right: 12px;
  width: 32px;
  height: 32px;
  border-radius: 50%;
  background-color: #ffffff;
  border: none;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.15);
}

.conteudo {
  padding: 16px;
  display: flex;
  flex-direction: column;
  gap: 12px;
  min-height: 190px;
}

.cabecalho {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  gap: 8px;
}

.titulo {
  margin: 0;
  font-size: 16px;
  font-weight: 600;
  color: #1a202c;
  line-height: 1.2;
  text-align: left;
}

.preco {
  font-size: 18px;
  font-weight: 700;
  color: #0f172a;
  white-space: nowrap;
}

.descricao {
  margin: 0;
  color: #475569;
  font-size: 14px;
  line-height: 1.4;
  text-align: left;
  min-height: 40px;
}

.localizacao {
  display: flex;
  align-items: flex-start;
  gap: 6px;
  font-size: 13px;
  color: #64748b;
  min-height: 32px;
  text-align: left;
}

.localizacao svg {
  flex-shrink: 0;
  margin-top: 2px;
}

.btn-anuncio {
  display: block;
  box-sizing: border-box;
  width: 100%;
  padding: 10px;
  background-color: #ffffff;
  border: 1px solid #cbd5e1;
  border-radius: 8px;
  font-size: 14px;
  font-weight: 600;
  color: #0f172a;
  cursor: pointer;
  margin-top: 4px;
  transition: background-color 0.2s;
  text-decoration: none;
}

.btn-anuncio:hover {
  background-color: #f8fafc;
}
</style>
