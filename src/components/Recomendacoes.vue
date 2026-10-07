<script setup lang="ts">
export interface TrendingItem {
  title: string
  caption: string
  accent: string
  poster: string
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
          <img v-if="item.poster" :src="item.poster" :alt="`Poster de ${item.title}`" class="trending-image">
          <span class="happy-overlay" aria-hidden="true">😊</span>
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
  color: var(--accent-pink);
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
  width: 100%;
  max-width: 320px;
  margin-inline: auto;
  transition: transform 0.25s ease;
}

.trending-poster {
  position: relative;
  width: 100%;
  aspect-ratio: 4 / 5;
  border-radius: 24px;
  border: 1px solid rgba(71, 232, 255, 0.2);
  overflow: hidden;
  box-shadow: inset 0 0 0 1px rgba(255, 255, 255, 0.04);
  transition: border-color 0.25s ease, box-shadow 0.25s ease;
}

.trending-poster::before {
  content: '';
  position: absolute;
  inset: 0;
  z-index: 1;
  background: linear-gradient(180deg, rgba(7, 9, 14, 0.06), rgba(7, 9, 14, 0.66));
}

.trending-image {
  position: absolute;
  inset: 0;
  z-index: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: opacity 0.3s ease, transform 0.35s ease;
}

.happy-overlay {
  position: absolute;
  inset: 0;
  z-index: 2;
  display: grid;
  place-items: center;
  color: var(--accent-gold);
  font-size: 4rem;
  line-height: 1;
  opacity: 0;
  pointer-events: none;
  text-shadow: 0 0 24px rgba(255, 229, 106, 0.9);
  transform: scale(0.65) rotate(-12deg);
  transition: opacity 0.25s ease, transform 0.35s cubic-bezier(0.2, 0.8, 0.2, 1);
}

.play-button {
  position: absolute;
  z-index: 3;
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

@media (hover: hover) {
  .trending-card:hover {
    transform: translateY(-6px);
  }

  .trending-card:hover .trending-poster {
    border-color: rgba(71, 232, 255, 0.72);
    box-shadow: 0 18px 34px rgba(0, 0, 0, 0.3), 0 0 24px rgba(71, 232, 255, 0.16);
  }

  .trending-card:hover .trending-image {
    opacity: 0.4;
    transform: scale(1.06);
  }

  .trending-card:hover .happy-overlay {
    animation: happy-emoji-peek 1.25s ease-out both;
  }
}

@media (prefers-reduced-motion: reduce) {
  .trending-card,
  .trending-poster,
  .trending-image,
  .happy-overlay {
    transition: none;
  }

  .trending-card:hover,
  .trending-card:hover .trending-image {
    transform: none;
  }

  .trending-card:hover .happy-overlay {
    animation: none;
    opacity: 1;
    transform: none;
  }
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
