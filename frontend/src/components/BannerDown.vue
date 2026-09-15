<template>
  <div class="mainHeader">
    <div class="insideImage">
      <h2 class="titleInsideImage">Tem roupas que não usa mais?</h2>
      <p class="pInsideImage">
        Dê uma nova vida às suas peças e ganhe dinheiro. Anuncie de forma rápida, segura e ajude a promover a moda circular.
      </p>
      <button class="ButtonInsideImage">
        <span class="icon">+</span> Criar anúncio
      </button>
    </div>

    <div class="imageContainer">
      <!-- Substitua a URL da imagem abaixo pela URL ou caminho da sua imagem da caixa com roupas -->
      <img 
        src="https://images.unsplash.com/photo-1544816155-12df9643f363?q=80&w=600&auto=format&fit=crop" 
        alt="Caixa com roupas" 
        class="circleImage"
      />
    </div>
  </div>
</template>

<script>
export default {
  name: 'BannerDown'
}
</script>

<style scoped>
.mainHeader {
  height: 380px;
  margin: 20px 10px 20px 10px;
  border-radius: 12px;
  background-color: #E6EEFA; /* Tom azul bem suave do fundo */
  
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 80px;
  box-sizing: border-box;
}

.insideImage {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  max-width: 500px;
  text-align: left;
}

.titleInsideImage {
  font-size: 32px;
  font-weight: 700;
  color: #111827;
  margin: 0 0 16px 0;
  line-height: 1.2;
}

.pInsideImage {
  font-size: 16px;
  color: #4B5563;
  margin: 0 0 28px 0;
  line-height: 1.5;
}

.ButtonInsideImage {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
  background-color: #333D4B; /* Cor grafite/escuro do botão */
  color: #FFFFFF;
  border: none;
  border-radius: 8px;
  padding: 12px 20px;
  font-size: 15px;
  font-weight: 600;
  cursor: pointer;
  transition: background-color 0.2s ease;
}

.ButtonInsideImage:hover {
  background-color: #1F2937;
}

.icon {
  font-size: 18px;
  font-weight: bold;
  line-height: 1;
}

.imageContainer {
  display: flex;
  align-items: center;
  justify-content: center;
}

.circleImage {
  width: 280px;
  height: 280px;
  border-radius: 50%;
  object-fit: cover;
  border: 4px solid #FFFFFF; /* Borda branca ao redor da imagem circular */
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.05);
}
</style>