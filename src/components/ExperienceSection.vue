<script setup lang="ts">
interface Role {
  period: string;
  title: string;
  org: string;
  bullets: string[];
}

const roles: Role[] = [
  {
    period: "01/2026 – 03/2026",
    title: "Responsável por Tecnologia (Full Stack / TI)",
    org: "Entidade Descentralizada Municipal Terminal de Ônibus, La Paz",
    bullets: [
      "Gestão orçamentária da área de TI e coordenação com fornecedores.",
      "Supervisão da equipe de hardware, manutenção, estagiário e desenvolvedor.",
      "Condução de reuniões de levantamento de requisitos com áreas solicitantes.",
    ],
  },
  {
    period: "01/2025 – 12/2025",
    title: "Encarregado por Monitoramento e Desenvolvedor de Sistemas",
    org: "Entidade Descentralizada Municipal Terminal de Ônibus, La Paz",
    bullets: [
      "Sistemas Full Stack com Angular 16, NestJS e PostgreSQL, incl. gestão de almoxarifado.",
      "Apresentação de avanços em reuniões periódicas e ajuste contínuo com feedback.",
      "Monitoramento de câmeras de segurança e apoio ao público.",
    ],
  },
  {
    period: "01/2024 – 12/2024",
    title: "Desenvolvedor Full Stack e Administrador de Banco de Dados",
    org: "Universidade Tecnológica Boliviana (UTB) — Depto. de Pesquisa",
    bullets: [
      "Biblioteca Virtual e Repositório Acadêmico da UTB, com painel administrativo.",
      "Colaboração no projeto SABIO (orientação vocacional com diadema EEG).",
      "Modelagem e administração de bancos de dados para métricas de uso.",
    ],
  },
  {
    period: "01/2024 – 12/2024 · estágio paralelo",
    title: "Estagiário Desenvolvedor Full Stack (Projeto de TCC)",
    org: "Sub-prefeitura Municipal de La Paz",
    bullets: [
      "Sistema \"Praça Digital\" para reserva de espaços públicos com upload de documentos.",
      "Painel administrativo: habilitação de espaços, sanções, relatórios e dashboards.",
      "Mapas interativos com QGIS. Stack: Laravel, AngularJS, Git, Bootstrap.",
    ],
  },
];
</script>

<template>
  <section id="experiencia">
    <div class="container">
      <h2 class="section-heading">Experiência</h2>
      <ol class="timeline">
        <li v-for="r in roles" :key="r.title" class="timeline__item">
          <span class="mono timeline__period">{{ r.period }}</span>
          <div class="timeline__body">
            <h3 class="timeline__title">{{ r.title }}</h3>
            <p class="timeline__org">{{ r.org }}</p>
            <ul class="timeline__bullets">
              <li v-for="b in r.bullets" :key="b">{{ b }}</li>
            </ul>
          </div>
        </li>
      </ol>
    </div>
  </section>
</template>

<style scoped>
.timeline {
  list-style: none;
  margin: 0;
  padding: 0;
  display: flex;
  flex-direction: column;
}

.timeline__item {
  display: grid;
  grid-template-columns: 150px 1fr;
  gap: 28px;
  padding: 28px 0;
  border-top: 1px solid var(--line);
}

.timeline__item:first-child {
  border-top: none;
}

.timeline__period {
  color: var(--accent);
  padding-top: 3px;
}

.timeline__title {
  font-size: 18px;
  margin-bottom: 4px;
}

.timeline__org {
  font-size: 14px;
  margin-bottom: 14px;
  color: var(--text-muted);
}

.timeline__bullets {
  margin: 0;
  padding-left: 18px;
  display: flex;
  flex-direction: column;
  gap: 6px;
}

.timeline__bullets li {
  font-size: 14.5px;
  color: var(--text-muted);
}

@media (max-width: 640px) {
  .timeline__item {
    grid-template-columns: 1fr;
    gap: 10px;
  }
}
</style>
