<template>
  <div class="card-anuncio">
    <div class="imagem-container">
      <img src="https://via.placeholder.com/300x330" alt="Calça Jeans" class="imagem" />
      <button class="btn-favorito" aria-label="Favoritar">
        <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="#666" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
          <path d="M20.84 4.61a5.5 5.5 0 0 0-7.78 0L12 5.67l-1.06-1.06a5.5 5.5 0 0 0-7.78 7.78l1.06 1.06L12 21.23l8.78-8.78 1.06-1.06a5.5 5.5 0 0 0 0-7.78z"></path>
        </svg>
      </button>
    </div>

    <div class="conteudo">
      <div class="cabecalho">
        <h3 class="titulo">Calça Jeans Levi's 501</h3>
        <span class="preco">R$ 150</span>
      </div>

      <div class="tags">
        <span class="tag">Tam 40</span>
        <span class="tag">Bom estado</span>
      </div>

      <div class="localizacao">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="#666" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
          <path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0 1 18 0z"></path>
          <circle cx="12" cy="10" r="3"></circle>
        </svg>
        <span>Rio de Janeiro, RJ</span>
      </div>

      <button class="btn-anuncio">Ver anúncio</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "AnuncioModal"
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

.imagem {
  width: 100%;
  height: 100%;
  object-fit: cover;
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
}

.preco {
  font-size: 18px;
  font-weight: 700;
  color: #0f172a;
  white-space: nowrap;
}

.tags {
  display: flex;
  gap: 8px;
}

.tag {
  background-color: #e8eef9;
  color: #4a6572;
  font-size: 12px;
  padding: 4px 10px;
  border-radius: 12px;
  font-weight: 500;
}

.localizacao {
  display: flex;
  align-items: center;
  gap: 6px;
  font-size: 13px;
  color: #64748b;
}

.btn-anuncio {
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
}

.btn-anuncio:hover {
  background-color: #f8fafc;
}
</style>