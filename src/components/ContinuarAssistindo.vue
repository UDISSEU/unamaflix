<script setup lang="ts">
export interface ContinueWatchingItem {
  title: string
  genre: string
  progress: number
  gradient: string
}

defineProps<{
  items: ContinueWatchingItem[]
}>()
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
          <span class="mini-percent">{{ item.progress }}%</span>
        </div>
        <div class="mini-info">
          <strong>{{ item.title }}</strong>
          <span>{{ item.genre }}</span>
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
  border: 1px solid rgba(255, 255, 255, 0.07);
  background: rgba(255, 255, 255, 0.02);
  border-radius: 24px;
}

.mini-poster {
  position: relative;
  width: 132px;
  height: 106px;
  border-radius: 18px;
  overflow: hidden;
  flex-shrink: 0;
}

.mini-poster::before {
  content: '';
  position: absolute;
  inset: 0;
  background: linear-gradient(180deg, rgba(17, 20, 29, 0.08), rgba(11, 14, 23, 0.7));
}

.mini-percent {
  position: absolute;
  right: 12px;
  bottom: 10px;
  z-index: 1;
  color: #fff;
  font-size: 0.82rem;
  font-weight: 700;
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

.progress-track {
  width: 100%;
  height: 8px;
  border-radius: 999px;
  background: rgba(255, 255, 255, 0.1);
  overflow: hidden;
}

.progress-track span {
  display: block;
  height: 100%;
  border-radius: inherit;
  background: linear-gradient(90deg, #ff8b4d, #ffb573);
}

@media (max-width: 980px) {
  .movie-row {
    grid-template-columns: 1fr;
  }
}
</style>
