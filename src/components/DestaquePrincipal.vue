<template>
  <section class="hero">
    <div class="hero-copy">
      <span class="eyebrow">Em alta agora</span>
      <h1>O reino das sombras não conhece perdão.</h1>
      <p>
        Uma jornada intensa de traição, coragem e sobrevivência, repleta de cenas eletrizantes
        e momentos que vão te prender do começo ao fim.
      </p>

      <div class="cta-row">
        <button class="primary-button large">▶ Assistir</button>
        <button class="secondary-button large">+ Minha lista</button>
      </div>

      <div class="meta-row">
        <span>4.9 ★</span>
        <span>2026</span>
        <span>Drama • Ação</span>
        <span>108 min</span>
      </div>
    </div>

    <div class="hero-visual" aria-label="Poster do filme do destaque">
      <div class="poster-glow"></div>
      <div class="movie-card large-card">
        <img src="/sombra.jpeg" alt="Poster de Sombras do Norte" class="featured-poster">
        <div class="poster-overlay"></div>
        <span class="happy-overlay" aria-hidden="true">😊</span>
        <div class="poster-content">
          <span class="tag">Top 10</span>
          <h2>Sombras do Norte</h2>
        </div>
        <div class="floating-badge info-badge">
          <span class="tiny-label">Nota</span>
          <strong>9.7</strong>
        </div>
        <div class="floating-badge genre-badge">
          <span class="tiny-label">Gênero</span>
          <strong>Fantasia</strong>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.hero {
  display: grid;
  grid-template-columns: 1.1fr 0.9fr;
  gap: 32px;
  align-items: center;
  min-height: 560px;
  padding: 16px 6px 0;
}

.hero-copy {
  display: flex;
  flex-direction: column;
  gap: 18px;
}

.eyebrow {
  display: inline-flex;
  width: fit-content;
  align-items: center;
  padding: 8px 14px;
  border-radius: 999px;
  background: rgba(71, 232, 255, 0.1);
  border: 1px solid rgba(71, 232, 255, 0.32);
  color: var(--accent-cyan);
  font-size: 0.72rem;
  letter-spacing: 0.12em;
  text-transform: uppercase;
}

.hero-copy h1 {
  margin: 0;
  font-size: clamp(3rem, 4vw, 5.5rem);
  line-height: 0.96;
  letter-spacing: -0.06em;
  max-width: 640px;
  color: #f5f7ff;
}

.hero-copy p {
  margin: 0;
  max-width: 620px;
  color: rgba(234, 239, 255, 0.72);
  font-size: 1.08rem;
  line-height: 1.7;
}

.cta-row,
.meta-row {
  display: flex;
  align-items: center;
  gap: 16px;
  flex-wrap: wrap;
}

.meta-row {
  margin-top: 6px;
}

.meta-row span {
  color: rgba(255, 255, 255, 0.75);
  font-size: 0.9rem;
}

.primary-button,
.secondary-button {
  min-height: 52px;
  padding: 0 28px;
  border: 0;
  border-radius: 999px;
  cursor: pointer;
  font: inherit;
}

.primary-button {
  background: linear-gradient(135deg, var(--accent-pink), #ff8a4c);
  color: white;
  font-weight: 700;
  box-shadow: 0 14px 28px rgba(255, 79, 154, 0.32);
}

.secondary-button {
  background: rgba(255, 255, 255, 0.08);
  color: white;
  border: 1px solid rgba(71, 232, 255, 0.28);
}

.hero-visual {
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 500px;
}

.poster-glow {
  position: absolute;
  inset: 40px 80px 50px 80px;
  border-radius: 40px;
  background:
    radial-gradient(circle at 40% 42%, rgba(71, 232, 255, 0.24), transparent 62%),
    radial-gradient(circle at 62% 58%, rgba(255, 79, 154, 0.25), transparent 68%);
  filter: blur(18px);
}

.movie-card {
  position: relative;
  width: min(440px, 90%);
  height: 520px;
  border-radius: 34px;
  overflow: hidden;
  border: 1px solid rgba(71, 232, 255, 0.34);
  background: linear-gradient(160deg, rgba(9, 12, 17, 0.16), rgba(8, 10, 17, 0));
  box-shadow: 0 34px 52px rgba(0, 0, 0, 0.46);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.poster-overlay {
  position: absolute;
  inset: 0;
  z-index: 1;
  background:
    linear-gradient(180deg, rgba(12, 15, 25, 0.02) 18%, rgba(8, 10, 17, 0.82) 100%),
    linear-gradient(135deg, rgba(255, 79, 154, 0.12), transparent 52%, rgba(71, 232, 255, 0.16));
}

.movie-card::before {
  content: '';
  position: absolute;
  inset: 0;
  background:
    linear-gradient(180deg, rgba(255, 255, 255, 0.1), transparent 30%),
    radial-gradient(circle at 15% 15%, rgba(255, 255, 255, 0.22), transparent 20%),
    linear-gradient(135deg, rgba(21, 27, 38, 0.8), rgba(12, 14, 24, 0.22));
}

.featured-poster {
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: opacity 0.3s ease, transform 0.45s ease;
}

.happy-overlay {
  position: absolute;
  inset: 0;
  z-index: 2;
  display: grid;
  place-items: center;
  color: var(--accent-gold);
  font-size: 5rem;
  line-height: 1;
  opacity: 0;
  pointer-events: none;
  text-shadow: 0 0 28px rgba(255, 229, 106, 0.9);
  transform: scale(0.65) rotate(-12deg);
  transition: opacity 0.25s ease, transform 0.35s cubic-bezier(0.2, 0.8, 0.2, 1);
}

.poster-content {
  position: absolute;
  inset: auto 28px 28px 28px;
  z-index: 3;
}

.tag {
  display: inline-block;
  padding: 7px 12px;
  border-radius: 999px;
  background: rgba(71, 232, 255, 0.22);
  border: 1px solid rgba(71, 232, 255, 0.48);
  color: #fff;
  font-size: 0.68rem;
  text-transform: uppercase;
  letter-spacing: 0.12em;
}

.poster-content h2 {
  margin: 16px 0 0;
  font-size: clamp(2.4rem, 2.2vw, 3.5rem);
  line-height: 0.9;
  letter-spacing: -0.06em;
  color: white;
}

@media (hover: hover) {
  .movie-card:hover {
    transform: translateY(-7px);
    box-shadow: 0 42px 64px rgba(0, 0, 0, 0.55);
  }

  .movie-card:hover .featured-poster {
    opacity: 0.4;
    transform: scale(1.04);
  }

  .movie-card:hover .happy-overlay {
    animation: happy-emoji-peek 1.25s ease-out both;
  }
}

@media (prefers-reduced-motion: reduce) {
  .movie-card,
  .featured-poster,
  .happy-overlay {
    transition: none;
  }

  .movie-card:hover,
  .movie-card:hover .featured-poster {
    transform: none;
  }

  .movie-card:hover .happy-overlay {
    animation: none;
    opacity: 1;
    transform: none;
  }
}

.floating-badge {
  position: absolute;
  z-index: 3;
  display: flex;
  flex-direction: column;
  gap: 4px;
  padding: 14px 16px;
  border: 1px solid rgba(71, 232, 255, 0.26);
  background: rgba(8, 18, 30, 0.76);
  backdrop-filter: blur(8px);
  border-radius: 18px;
  color: #fff;
  box-shadow: 0 20px 30px rgba(0, 0, 0, 0.2);
}

.info-badge {
  top: 18px;
  right: 18px;
}

.genre-badge {
  top: 18px;
  left: 18px;
}

.tiny-label {
  font-size: 0.68rem;
  color: rgba(255, 255, 255, 0.55);
  text-transform: uppercase;
  letter-spacing: 0.12em;
}

.floating-badge strong {
  font-size: 1.1rem;
}

.info-badge strong {
  color: var(--accent-gold);
}

.genre-badge strong {
  color: var(--accent-cyan);
}

@media (max-width: 980px) {
  .hero {
    grid-template-columns: 1fr;
    min-height: auto;
  }
}

@media (max-width: 640px) {
  .hero-copy h1 {
    font-size: 2.5rem;
  }

  .movie-card {
    height: 420px;
  }

  .floating-badge {
    transform: scale(0.9);
  }
}
</style>
