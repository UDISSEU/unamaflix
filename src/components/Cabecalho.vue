<script setup lang="ts">
defineProps<{
  navItems: string[]
}>()
</script>

<template>
  <header class="topbar">
    <div class="brand-wrap">
      <div class="brand-mark">C</div>
      <span class="brand-name">CINEHUB</span>
    </div>

    <nav class="main-nav" aria-label="Navegação principal">
      <a v-for="item in navItems" :key="item" href="#" class="nav-link">{{ item }}</a>
    </nav>

    <div class="utility-actions">
      <button class="ghost-button">Buscar</button>
      <button class="primary-button">Assista agora</button>
    </div>
  </header>
</template>

<style scoped>
.topbar {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 20px;
  padding-bottom: 18px;
}

.brand-wrap {
  display: flex;
  align-items: center;
  gap: 12px;
}

.brand-mark {
  width: 40px;
  height: 40px;
  display: grid;
  place-items: center;
  border-radius: 12px;
  background: linear-gradient(135deg, var(--accent-pink), #ff9f43 58%, var(--accent-gold));
  color: #fff;
  font-weight: 800;
  box-shadow: 0 0 22px rgba(255, 79, 154, 0.28);
}

.brand-name {
  color: #fff;
  letter-spacing: 0.2em;
  font-size: 0.78rem;
  font-weight: 700;
}

.main-nav {
  display: flex;
  align-items: center;
  gap: 28px;
  flex-wrap: wrap;
  justify-content: center;
}

.nav-link {
  position: relative;
  padding: 8px 0;
  color: rgba(255, 255, 255, 0.7);
  text-decoration: none;
  font-size: 0.92rem;
  transition: color 0.2s ease;
}

.nav-link::after {
  position: absolute;
  right: 0;
  bottom: 0;
  left: 0;
  height: 2px;
  background: var(--accent-cyan);
  box-shadow: 0 0 10px rgba(71, 232, 255, 0.75);
  content: '';
  transform: scaleX(0);
  transform-origin: left;
  transition: transform 0.2s ease;
}

.nav-link:first-child {
  color: var(--accent-cyan);
}

.nav-link:first-child::after,
.nav-link:hover::after {
  transform: scaleX(1);
}

.nav-link:hover {
  color: var(--accent-cyan);
  background: transparent;
}

.utility-actions {
  display: flex;
  align-items: center;
  gap: 12px;
}

button {
  border: 0;
  border-radius: 999px;
  cursor: pointer;
  transition: transform 0.2s ease, box-shadow 0.2s ease;
  font: inherit;
}

button:hover {
  transform: translateY(-1px);
}

.primary-button,
.secondary-button,
.ghost-button {
  min-height: 46px;
  padding: 0 22px;
}

.primary-button {
  background: linear-gradient(135deg, var(--accent-pink), #ff8a4c);
  color: white;
  font-weight: 700;
  box-shadow: 0 12px 28px rgba(255, 79, 154, 0.3);
}

.secondary-button {
  background: rgba(255, 255, 255, 0.08);
  color: white;
  border: 1px solid rgba(71, 232, 255, 0.28);
}

.ghost-button {
  background: transparent;
  color: rgba(255, 255, 255, 0.7);
  border: 1px solid rgba(71, 232, 255, 0.2);
}

.ghost-button:hover {
  color: var(--accent-cyan);
  border-color: rgba(71, 232, 255, 0.6);
  box-shadow: 0 0 18px rgba(71, 232, 255, 0.14);
}

@media (max-width: 980px) {
  .topbar {
    flex-wrap: wrap;
  }
}

@media (max-width: 640px) {
  .brand-name {
    letter-spacing: 0.1em;
    font-size: 0.68rem;
  }

  .main-nav {
    width: 100%;
    justify-content: flex-start;
    gap: 12px 18px;
  }

  .utility-actions {
    width: 100%;
    justify-content: space-between;
  }
}
</style>
