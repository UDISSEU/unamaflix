<script setup lang="ts">
export interface TrendingItem {
  title: string
  caption: string
  accent: string
}

defineProps<{
  items: TrendingItem[]
}>()
</script>

<template>
  <section class="row-section">
    <div class="section-header">
      <h3>Para você</h3>
      <a href="#">Explorar</a>
    </div>

    <div class="trending-grid">
      <article v-for="item in items" :key="item.title" class="trending-card">
        <div class="trending-poster" :style="{ background: `linear-gradient(180deg, ${item.accent} 0%, rgba(13,18,30,0.22) 100%)` }">
          <span class="play-button">▶</span>
        </div>
        <div class="trending-body">
          <h4>{{ item.title }}</h4>
          <p>{{ item.caption }}</p>
        </div>
      </article>
    </div>
  </section>
</template>

<style scoped>
.row-section {
  display: flex;
  flex-direction: column;
  gap: 18px;
}

.section-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 12px;
}

.section-header h3 {
  margin: 0;
  color: #f5f7ff;
  font-size: 1.75rem;
  letter-spacing: -0.04em;
}

.section-header a {
  color: #ffb89c;
  text-decoration: none;
  font-weight: 600;
}

.trending-grid {
  display: grid;
  gap: 20px;
  grid-template-columns: repeat(4, minmax(0, 1fr));
}

.trending-card {
  display: flex;
  flex-direction: column;
  gap: 14px;
}

.trending-poster {
  position: relative;
  height: 280px;
  border-radius: 24px;
  border: 1px solid rgba(255, 255, 255, 0.08);
  overflow: hidden;
  box-shadow: inset 0 0 0 1px rgba(255, 255, 255, 0.04);
}

.trending-poster::before {
  content: '';
  position: absolute;
  inset: 0;
  background: linear-gradient(180deg, rgba(7, 9, 14, 0.06), rgba(7, 9, 14, 0.66));
}

.play-button {
  position: absolute;
  left: 18px;
  bottom: 18px;
  width: 42px;
  height: 42px;
  display: grid;
  place-items: center;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.18);
  backdrop-filter: blur(6px);
  border: 1px solid rgba(255, 255, 255, 0.14);
  color: #fff;
  font-size: 0.9rem;
}

.trending-body {
  display: flex;
  flex-direction: column;
  gap: 6px;
}

.trending-body h4 {
  margin: 0;
  color: #f4f6ff;
  font-size: 1.35rem;
  letter-spacing: -0.04em;
}

.trending-body p {
  margin: 0;
  color: rgba(255, 255, 255, 0.64);
}

@media (max-width: 980px) {
  .trending-grid {
    grid-template-columns: repeat(2, minmax(0, 1fr));
  }
}

@media (max-width: 640px) {
  .trending-grid {
    grid-template-columns: 1fr;
  }
}
</style>
