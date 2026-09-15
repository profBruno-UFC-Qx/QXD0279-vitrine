<template>
  <div class="mainHeader">
    <div class="insideImage">
      <h2 class="titleInsideImage">Encontre sua próxima peça favorita</h2>
      <p class="pInsideImage">
        Compre, venda e troque roupas usadas com segurança e estilo em nosso marketplace de moda circular.
      </p>
      <button class="ButtonInsideImage">Ver anúncios</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'AppHomeHeader',
};
</script>

<style scoped>
/* Reseta margens para evitar surpresas se o seu app já não o fizer */
.mainHeader,
.insideImage,
.titleInsideImage,
.pInsideImage,
.ButtonInsideImage {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.mainHeader {
  height: 450px;
  /* Espaçamento externo do banner */
  margin: 20px 10px 20px 10px;
  border-radius: 10px;

  /* Configuração de Fundo com Imagem e Sobreposição Clara (light overlay) */
  /* O linear-gradient cria a sobreposição clara para legibilidade */
  background-image: 
    linear-gradient(to right, rgba(255, 255, 255, 0.7), rgba(255, 255, 255, 0.4)),
    url('https://lh3.googleusercontent.com/aida-public/AB6AXuBaX1x7dOSM8RmPfdEHObpeecXGq7tYMr-TYzXLKMxvAW2_1IZo1nCLd1UFBVpcFbJzY13sMz6LGISRi5GQ0hQYVlHq4jS4c92u6-dhWNPTr5m3FcGMU_KXyl113azTFea7rFa0GlG33GFkTw2gjs0liwVr4q1T0HYpydFfsqULAswbgFOm8P6Y9Z9pZWWex4wBdw9brYYvOEUUrgRtSzFqlnnN48pwnN4oDkSqNhCbvxi-XiIPvMTCuw');
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;

  /* IMPORTANTE: Remova a opacity geral daqui, pois ela clareia tudo. 
     A sobreposição é feita pelo linear-gradient no background-image. */
  /* opacity: 0.6; -- REMOVIDO */
  overflow: hidden; /* Garante que os filhos respeitem o border-radius */

  /* Layout do Container Principal */
  display: flex;
  align-items: center; /* Centraliza verticalmente o conteúdo */
  justify-content: flex-start; /* Alinha o conteúdo à esquerda */
}

.insideImage {
  /* Alinhamento de conteúdo */
  color: #1a1c24; /* Um preto/cinza muito escuro para o texto principal */
  display: flex;
  flex-direction: column;
  align-items: flex-start; /* Alinha o texto e o botão à esquerda */

  /* Espaçamento e Largura */
  padding-left: 60px; /* Alinhamento do conteúdo à esquerda */
  padding-right: 20px; /* Margem de segurança à direita */
  max-width: 600px; /* Limita a largura do texto para legibilidade */
  text-align: left; /* Garante alinhamento de texto à esquerda */
}

.titleInsideImage {
  font-size: 40px; /* Título maior */
  font-weight: 700; /* Peso bold da fonte */
  line-height: 1.2; /* Espaçamento entre linhas ajustado */
  margin-bottom: 24px; /* Espaço até o parágrafo */
}

.pInsideImage {
  font-size: 16px; /* Tamanho do parágrafo */
  color: #5a6270; /* Um cinza para o parágrafo, conforme a foto */
  line-height: 1.6; /* Melhor legibilidade */
  margin-bottom: 36px; /* Espaço até o botão */
  max-width: 90%; /* Ajuste fino da largura do parágrafo */
}

.ButtonInsideImage {
  /* Estilo visual conforme a imagem */
  background-color: #1a1c24; /* Fundo escuro */
  color: #ffffff; /* Texto branco */
  font-size: 14px;
  font-weight: 600; /* Texto um pouco mais grosso */
  border: none; /* Remove bordas padrão */
  border-radius: 6px; /* Cantos arredondados */

  /* Preenchimento e Dimensionamento */
  padding: 12px 28px; /* Controla o tamanho do botão pelo preenchimento interno */
  cursor: pointer; /* Muda o cursor para mãozinha */
  transition: background-color 0.2s ease; /* Efeito suave no hover */
}

.ButtonInsideImage:hover {
  background-color: #2c2f3d; /* Um pouco mais claro no hover */
}

</style>