<template>
  <nav class="navbar">

    <!-- Logo -->
    <div class="logo">
      Vitrine
    </div>

    <!-- Barra de pesquisa -->
    <div class="search-container">
      <svg
        class="search-icon"
        xmlns="http://www.w3.org/2000/svg"
        viewBox="0 0 24 24"
      >
        <circle cx="11" cy="11" r="7"></circle>
        <line x1="16.65" y1="16.65" x2="21" y2="21"></line>
      </svg>

      <input
        type="text"
        placeholder="Buscar roupas..."
        v-model="search"
      />
    </div>

    <!-- Ações -->
    <div class="actions">

      <button class="announce-button" @click="anunciarRoupa">
        Anunciar roupa
      </button>

      <button class="profile-button" @click="abrirPerfil">
        <svg
          class="profile-icon"
          xmlns="http://www.w3.org/2000/svg"
          viewBox="0 0 24 24"
        >
          <circle cx="12" cy="8" r="3"></circle>
          <path d="M5 21c0-3.5 3-6 7-6s7 2.5 7 6"></path>
        </svg>
      </button>

    </div>

  </nav>
</template>

<script>
export default {
  name: "AppNavbar",

  data() {
    return {
      search: ""
    };
  },

  methods: {
    anunciarRoupa() {
      console.log("Abrir tela de anúncio");
    },

    abrirPerfil() {
      console.log("Abrir perfil");
    }
  }
};
</script>

<style scoped>
* {
  box-sizing: border-box;
}

.navbar {
  width: 100%;
  height: 56px; /* Ajuste aqui a altura desejada (ex: 48px, 56px, etc.) */

  display: flex;
  align-items: center;

  

  background-color: #ffffff;
  border-bottom: 1px solid #e5e7eb;

  font-family: Arial, sans-serif;

  box-sizing: border-box;

  overflow: hidden;
}

/* Logo */

.logo {
  font-size: 24px;
  font-weight: 700;
  color: #1f2937;

  width: 200px;
  flex-shrink: 0;
}

/* Pesquisa */

.search-container {
  height: 40px;

  width: 100%;
  max-width: 430px;

  display: flex;
  align-items: center;

  border: 1px solid #d1d5db;
  border-radius: 8px;

  background-color: #f9fafb;



  flex-shrink: 1;
}

.search-icon {
  width: 20px;
  height: 20px;

  margin-right: 8px;

  stroke: #4b5563;
  fill: none;
  stroke-width: 2;

  flex-shrink: 0;
}

.search-container input {
  width: 100%;
  min-width: 0;

  border: none;
  outline: none;

  background: transparent;

  font-size: 16px;
  color: #374151;
}

.search-container input::placeholder {
  color: #9ca3af;
}

/* Ações */

.actions {
  margin-left: auto;

  display: flex;
  align-items: center;

  gap: 24px;

  flex-shrink: 0;
}

/* Botão anunciar */

.announce-button {
  height: 40px;

  padding: 0 24px;

  border: none;
  border-radius: 8px;

  background-color: #374151;
  color: white;

  font-size: 14px;
  font-weight: 600;

  cursor: pointer;

  transition: background-color 0.2s;

  white-space: nowrap;
}

.announce-button:hover {
  background-color: #1f2937;
}

/* Perfil */

.profile-button {
  width: 32px;
  height: 32px;

  padding: 0;

  border: none;
  background: transparent;

  cursor: pointer;

  flex-shrink: 0;
}

.profile-icon {
  width: 22px;
  height: 22px;

  stroke: #374151;
  fill: none;
  stroke-width: 1.8;
}
</style>