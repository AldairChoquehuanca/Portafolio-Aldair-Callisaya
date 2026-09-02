<script setup lang="ts">
const facts = [
  { label: "Formação", value: "Eng. de Sistemas —Universidade Tecnológica Boliviana (UTB), Bolívia" },
  { label: "Experiência", value: "2+ anos + estágio efetivado" },
  { label: "Idiomas", value: "Português avançado ·  Espanhol Fluente" },
  { label: "Disponibilidade", value: "Híbrido ou presencial" },
];
</script>

<template>
  <section id="sobre">
    <div class="container about">
      <h2 class="section-heading">Sobre mim</h2>
      <p class="about__text">
        Comecei como estagiário bolsista na Universidade Tecnológica Boliviana (UTB), onde fui efetivado como
        desenvolvedor ainda durante a graduação, com estágio paralelo na
        Sub-prefeitura Municipal de La Paz. No ano seguinte fui convidado a
        integrar uma instituição da prefeitura, e em cerca de um ano fui
        promovido a Responsável por Tecnologia — coordenando equipe técnica e
        fornecedores. Tenho perfil autodidata e experiência sólida em
        modelagem de banco de dados e levantamento de requisitos junto a
        áreas de negócio. Atualmente radicado em São Paulo, em busca de novas
        oportunidades como Desenvolvedor Full Stack.
      </p>

      <dl class="about__facts">
        <div v-for="f in facts" :key="f.label" class="about__fact">
          <dt class="mono">{{ f.label }}</dt>
          <dd>{{ f.value }}</dd>
        </div>
      </dl>
    </div>
  </section>
</template>

<style scoped>
.about {
  display: grid;
  grid-template-columns: 1.3fr 1fr;
  gap: 56px;
}

.about__text {
  max-width: none;
  font-size: 15.5px;
}

.about__facts {
  display: flex;
  flex-direction: column;
  gap: 20px;
  margin: 0;
  border-left: 1px solid var(--line);
  padding-left: 24px;
}

.about__fact dt {
  color: var(--accent);
  margin-bottom: 4px;
}

.about__fact dd {
  margin: 0;
  font-size: 15px;
}

@media (max-width: 780px) {
  .about {
    grid-template-columns: 1fr;
    gap: 32px;
  }
  .about__facts {
    border-left: none;
    padding-left: 0;
    border-top: 1px solid var(--line);
    padding-top: 24px;
  }
}
</style>
