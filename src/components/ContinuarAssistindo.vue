<script setup lang="ts">
import { computed } from 'vue'

export interface ContinueWatchingItem {
  title: string
  genre: string
  progress: number
  gradient: string
  poster: string
}

const props = defineProps<{
  items: ContinueWatchingItem[]
}>()

const highestProgress = computed(() => Math.max(...props.items.map((item) => item.progress)))
const lowestProgress = computed(() => Math.min(...props.items.map((item) => item.progress)))
</script>

<template>
  <section class="row-section">
    <div class="section-header">
      <h3>Continue assistindo</h3>
      <a href="#">Ver tudo</a>
    </div>

    <div class="movie-row">
      <article v-for="item in items" :key="item.title" class="mini-showcase">
        <div class="mini-poster" :style="{ background: item.gradient }">
          <img :src="item.poster" :alt="`Poster de ${item.title}`" class="mini-poster-image">
          <span class="happy-overlay" aria-hidden="true">😊</span>
        </div>
        <div class="mini-info">
          <strong>{{ item.title }}</strong>
          <span>{{ item.genre }}</span>
          <div class="progress-label">
            <span>Progresso</span>
            <strong>
              {{ item.progress }}%
              <span v-if="item.progress === highestProgress" class="progress-mood" role="img" aria-label="Maior progresso">🔥</span>
              <span v-else-if="item.progress === lowestProgress" class="progress-mood" role="img" aria-label="Menor progresso">😢</span>
            </strong>
          </div>
          <div class="progress-track">
            <span :style="{ width: item.progress + '%' }"></span>
          </div>
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

.movie-row {
  display: grid;
  gap: 20px;
  grid-template-columns: repeat(3, minmax(0, 1fr));
}

.mini-showcase {
  display: flex;
  gap: 16px;
  align-items: center;
  padding: 16px 18px;
  border: 1px solid rgba(71, 232, 255, 0.12);
  background: linear-gradient(120deg, rgba(71, 232, 255, 0.045), rgba(255, 79, 154, 0.025));
  border-radius: 24px;
  transition: transform 0.25s ease, border-color 0.25s ease, box-shadow 0.25s ease;
}

.mini-poster {
  position: relative;
  width: 96px;
  height: 120px;
  border-radius: 18px;
  overflow: hidden;
  flex-shrink: 0;
}

.mini-poster::before {
  content: '';
  position: absolute;
  inset: 0;
  z-index: 1;
  background: linear-gradient(180deg, rgba(17, 20, 29, 0.08), rgba(11, 14, 23, 0.7));
}

.mini-poster-image {
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
  font-size: 2.25rem;
  line-height: 1;
  opacity: 0;
  pointer-events: none;
  text-shadow: 0 0 18px rgba(255, 229, 106, 0.9);
  transform: scale(0.65) rotate(-12deg);
  transition: opacity 0.25s ease, transform 0.35s cubic-bezier(0.2, 0.8, 0.2, 1);
}

.mini-info {
  display: flex;
  flex: 1;
  flex-direction: column;
  gap: 8px;
  min-width: 0;
}

.mini-info strong {
  color: #fff;
  font-size: 1.1rem;
}

.mini-info span {
  color: rgba(255, 255, 255, 0.68);
  font-size: 0.9rem;
}

.progress-label {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-top: 2px;
  line-height: 1;
}

.mini-info .progress-label span {
  color: rgba(255, 255, 255, 0.58);
  font-size: 0.75rem;
}

.mini-info .progress-label strong {
  color: var(--accent-gold);
  font-size: 0.82rem;
}

.mini-info .progress-label strong .progress-mood {
  margin-left: 4px;
  font-size: 1rem;
}

.progress-track {
  width: 100%;
  height: 9px;
  border-radius: 999px;
  background: rgba(255, 255, 255, 0.1);
  overflow: hidden;
}

.progress-track span {
  position: relative;
  display: block;
  height: 100%;
  border-radius: inherit;
  background: linear-gradient(90deg, var(--accent-cyan), var(--accent-pink));
  box-shadow: 0 0 12px rgba(71, 232, 255, 0.36);
  transform: scaleX(0);
  transform-origin: left;
  animation: progress-fill 1s cubic-bezier(0.22, 0.8, 0.25, 1) forwards;
  transition: box-shadow 0.3s ease, filter 0.3s ease;
}

.progress-track span::after {
  position: absolute;
  inset: 0;
  width: 36%;
  border-radius: inherit;
  background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.8), transparent);
  content: '';
  transform: translateX(-140%);
}

@keyframes progress-fill {
  to {
    transform: scaleX(1);
  }
}

@keyframes progress-shine {
  to {
    transform: translateX(320%);
  }
}

@media (hover: hover) {
  .mini-showcase:hover {
    transform: translateY(-5px);
    border-color: rgba(71, 232, 255, 0.48);
    box-shadow: 0 16px 32px rgba(0, 0, 0, 0.24), 0 0 24px rgba(71, 232, 255, 0.1);
  }

  .mini-showcase:hover .mini-poster-image {
    opacity: 0.4;
    transform: scale(1.06);
  }

  .mini-showcase:hover .happy-overlay {
    animation: happy-emoji-peek 1.25s ease-out both;
  }

  .mini-showcase:hover .progress-track > span {
    filter: brightness(1.2);
    box-shadow: 0 0 18px rgba(71, 232, 255, 0.68);
  }

  .mini-showcase:hover .progress-track > span::after {
    animation: progress-shine 0.9s ease forwards;
  }
}

@media (prefers-reduced-motion: reduce) {
  .mini-showcase,
  .mini-poster-image,
  .happy-overlay {
    transition: none;
  }

  .mini-showcase:hover,
  .mini-showcase:hover .mini-poster-image {
    transform: none;
  }

  .mini-showcase:hover .happy-overlay {
    animation: none;
    opacity: 1;
    transform: none;
  }

  .progress-track span,
  .progress-track span::after {
    animation: none;
  }

  .progress-track span {
    transform: none;
  }
}

@media (max-width: 980px) {
  .movie-row {
    grid-template-columns: 1fr;
  }
}
</style>
