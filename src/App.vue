<script setup lang="ts">
import Cabecalho from './components/Cabecalho.vue'
import DestaquePrincipal from './components/DestaquePrincipal.vue'
import ContinuarAssistindo from './components/ContinuarAssistindo.vue'
import Recomendacoes from './components/Recomendacoes.vue'

const navItems = ['Início', 'Séries', 'Filmes', 'Novidades', 'Minha lista']

const continueWatching = [
  { title: 'A Espiã', genre: 'Ação', progress: 68, gradient: 'linear-gradient(135deg, #ff7a18, #af1a2d)' },
  { title: 'Névoa Negra', genre: 'Thriller', progress: 42, gradient: 'linear-gradient(135deg, #6044d9, #1d224f)' },
  { title: 'Dunas da Noite', genre: 'Ficção', progress: 85, gradient: 'linear-gradient(135deg, #1b9aaa, #190b50)' },
]

const trending = [
  { title: 'O Último Trovão', caption: 'Ação • 96 min', accent: '#ffb800' },
  { title: 'Vento em Fúria', caption: 'Drama • 124 min', accent: '#8ab4ff' },
  { title: 'Muralha 3', caption: 'Fantasia • 118 min', accent: '#ff6b6b' },
  { title: 'Nuvens do Amanhã', caption: 'Sci-Fi • 101 min', accent: '#5eead4' },
]
</script>

<template>
  <div class="page-shell">
    <Cabecalho :nav-items="navItems" />

    <main class="content">
      <DestaquePrincipal />
      <ContinuarAssistindo :items="continueWatching" />
      <Recomendacoes :items="trending" />
    </main>
  </div>
</template>

<style scoped>
.page-shell {
  width: min(1400px, calc(100% - 32px));
  margin: 20px auto;
  padding: 24px 26px 40px;
  border: 1px solid rgba(255, 255, 255, 0.08);
  border-radius: 28px;
  background: rgba(10, 11, 18, 0.86);
  box-shadow: 0 28px 80px rgba(0, 0, 0, 0.45);
  backdrop-filter: blur(10px);
}

.content {
  display: flex;
  flex-direction: column;
  gap: 34px;
}

@media (max-width: 640px) {
  .page-shell {
    width: min(100% - 18px, 1400px);
    padding: 18px 18px 26px;
    border-radius: 20px;
  }
}
</style>
