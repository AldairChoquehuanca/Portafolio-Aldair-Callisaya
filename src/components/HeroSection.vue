<script setup lang="ts">
</script>

<template>
  <section id="top" class="hero">
    <div class="container hero__grid">
      <div class="hero__copy">
        <p class="mono hero__eyebrow">La Paz, Bolívia → São Paulo, Brasil</p>
        <h1 class="hero__title">
          Aldair Kelvin<br />Choquehuanca Callisaya
        </h1>
        <p class="hero__role">
          Desenvolvedor Full Stack e Engenheiro de Sistemas. Trabalho com
          banco de dados, back-end e front-end, e venho me aprofundando
          também em análise de dados.
        </p>
        <div class="hero__actions">
          <a class="btn btn-primary" href="#projetos">Ver projetos</a>
          <!-- <a class="btn btn-ghost" href="mailto:callisayaaldair@gmail.com"
            >Falar comigo</a
          > -->
        </div>
      </div>

      <div class="hero__diagram" aria-hidden="true">
        <svg viewBox="0 0 320 280" fill="none">
          <line x1="160" y1="46" x2="70" y2="150" stroke="var(--line)" />
          <line x1="160" y1="46" x2="250" y2="150" stroke="var(--line)" />
          <line x1="70" y1="150" x2="160" y2="234" stroke="var(--line)" />
          <line x1="250" y1="150" x2="160" y2="234" stroke="var(--line)" />
          <line x1="70" y1="150" x2="250" y2="150" stroke="var(--line)" />

          <g>
            <circle cx="160" cy="46" r="34" fill="var(--surface)" stroke="var(--accent)" stroke-width="1.5" />
            <text x="160" y="42" text-anchor="middle" class="node-label">Front-End</text>
            <text x="160" y="55" text-anchor="middle" class="node-sub">Vue · React · Angular</text>
          </g>

          <g>
            <circle cx="70" cy="150" r="34" fill="var(--surface)" stroke="var(--accent)" stroke-width="1.5" />
            <text x="70" y="146" text-anchor="middle" class="node-label">Back-End</text>
            <text x="70" y="159" text-anchor="middle" class="node-sub">Node · NestJS</text>
          </g>

          <g>
            <circle cx="250" cy="150" r="34" fill="var(--surface)" stroke="var(--accent)" stroke-width="1.5" />
            <text x="250" y="146" text-anchor="middle" class="node-label">Back-End</text>
            <text x="250" y="159" text-anchor="middle" class="node-sub">PHP · Laravel</text>
          </g>

          <g>
            <circle cx="160" cy="234" r="34" fill="var(--accent-soft)" stroke="var(--accent)" stroke-width="1.5" />
            <text x="160" y="230" text-anchor="middle" class="node-label">Dados</text>
            <text x="160" y="243" text-anchor="middle" class="node-sub">SQL · Postgres</text>
          </g>
        </svg>
      </div>
    </div>
  </section>
</template>

<style scoped>
.hero {
  padding-top: 88px;
  border-bottom: 1px solid var(--line);
}

.hero__grid {
  display: grid;
  grid-template-columns: 1.15fr 0.85fr;
  gap: 48px;
  align-items: center;
}

.hero__eyebrow {
  color: var(--accent);
  margin-bottom: 18px;
}

.hero__title {
  font-size: 40px;
  margin-bottom: 20px;
}

.hero__role {
  font-size: 17px;
  margin-bottom: 32px;
}

.hero__actions {
  display: flex;
  gap: 12px;
  flex-wrap: wrap;
}

.hero__diagram svg {
  width: 100%;
  height: auto;
}

.node-label {
  font-family: var(--font-display);
  font-size: 12px;
  fill: var(--text);
}

.node-sub {
  font-family: var(--font-mono);
  font-size: 8px;
  fill: var(--text-muted);
}

@media (max-width: 780px) {
  .hero__grid {
    grid-template-columns: 1fr;
  }
  .hero__diagram {
    max-width: 280px;
    margin: 0 auto;
  }
  .hero__title {
    font-size: 30px;
  }
}
</style>
