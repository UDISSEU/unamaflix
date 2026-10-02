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
        <div class="poster-overlay"></div>
        <div class="poster-content">
          <span class="tag">Top 10</span>
          <h2>Sombras do Norte</h2>
        </div>
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
  background: rgba(255, 121, 90, 0.14);
  border: 1px solid rgba(255, 129, 90, 0.2);
  color: #ffb48d;
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
  background: linear-gradient(135deg, #ff5b77, #ff9d43);
  color: white;
  font-weight: 700;
  box-shadow: 0 14px 28px rgba(255, 102, 102, 0.35);
}

.secondary-button {
  background: rgba(255, 255, 255, 0.08);
  color: white;
  border: 1px solid rgba(255, 255, 255, 0.1);
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
  background: radial-gradient(circle at center, rgba(255, 92, 109, 0.32), rgba(16, 18, 28, 0) 68%);
  filter: blur(18px);
}

.movie-card {
  position: relative;
  width: min(440px, 90%);
  height: 520px;
  border-radius: 34px;
  overflow: hidden;
  border: 1px solid rgba(255, 255, 255, 0.18);
  background: linear-gradient(160deg, rgba(9, 12, 17, 0.16), rgba(8, 10, 17, 0));
  box-shadow: 0 34px 52px rgba(0, 0, 0, 0.46);
}

.poster-overlay {
  position: absolute;
  inset: 0;
  background:
    linear-gradient(180deg, rgba(12, 15, 25, 0.12), rgba(8, 10, 17, 0.78)),
    linear-gradient(135deg, rgba(255, 118, 94, 0.75), rgba(48, 22, 78, 0.1) 45%, rgba(17, 24, 36, 0.86) 100%);
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

.poster-content {
  position: absolute;
  inset: auto 28px 28px 28px;
  z-index: 1;
}

.tag {
  display: inline-block;
  padding: 7px 12px;
  border-radius: 999px;
  background: rgba(255, 255, 255, 0.12);
  border: 1px solid rgba(255, 255, 255, 0.12);
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

.floating-badge {
  position: absolute;
  display: flex;
  flex-direction: column;
  gap: 4px;
  padding: 14px 16px;
  border: 1px solid rgba(255, 255, 255, 0.1);
  background: rgba(13, 18, 28, 0.5);
  backdrop-filter: blur(8px);
  border-radius: 18px;
  color: #fff;
  box-shadow: 0 20px 30px rgba(0, 0, 0, 0.2);
}

.info-badge {
  right: 18px;
  bottom: 110px;
}

.genre-badge {
  left: 18px;
  bottom: 38px;
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
