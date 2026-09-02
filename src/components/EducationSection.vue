<script setup lang="ts">
const certifications = [
  { name: "Desenvolvimento e Automação de APIs", org: "UTB, La Paz", year: "2021" },
  { name: "Cloud Computing e Web Services", org: "UTB, La Paz", year: "2020" },
  { name: "Controle de Processos Automáticos", org: "Universidad de Tarapacá, Chile", year: "2022" },
];
</script>

<template>
  <section id="formacao">
    <div class="container formacao">
      <div>
        <h2 class="section-heading">Formação</h2>
        <div class="degree">
          <p class="degree__title">Bacharelado em Engenharia de Sistemas</p>
          <p class="mono degree__meta">UTB, Bolívia · 2020 – 2025</p>
        </div>

        <ul class="certs">
          <li v-for="c in certifications" :key="c.name">
            <span>{{ c.name }}</span>
            <span class="mono certs__meta">{{ c.org }} · {{ c.year }}</span>
          </li>
        </ul>
      </div>

      <div class="languages">
        <h3 class="mono skills__label">Idiomas</h3>
        <div class="languages__list">
          <div class="languages__item">
            <span>Espanhol</span>
            <span class="mono">Fluente</span>
          </div>
          <div class="languages__item">
            <span>Português</span>
            <span class="mono">Avançado</span>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.formacao {
  display: grid;
  grid-template-columns: 1.4fr 1fr;
  gap: 56px;
}

.degree {
  margin-bottom: 28px;
}

.degree__title {
  color: var(--text);
  font-size: 16px;
  margin-bottom: 4px;
}

.degree__meta {
  color: var(--text-muted);
}

.certs {
  list-style: none;
  margin: 0;
  padding: 0;
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.certs li {
  display: flex;
  flex-direction: column;
  gap: 2px;
  font-size: 14.5px;
  border-top: 1px solid var(--line);
  padding-top: 12px;
}

.certs__meta {
  color: var(--text-muted);
  font-size: 12px;
}

.skills__label {
  color: var(--accent);
  margin-bottom: 16px;
}

.languages__list {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.languages__item {
  display: flex;
  justify-content: space-between;
  border-bottom: 1px solid var(--line);
  padding-bottom: 10px;
  font-size: 14.5px;
}

@media (max-width: 720px) {
  .formacao {
    grid-template-columns: 1fr;
    gap: 32px;
  }
}
</style>
