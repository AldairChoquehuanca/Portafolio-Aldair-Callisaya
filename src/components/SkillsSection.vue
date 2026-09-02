<script setup lang="ts">
const groups = [
  {
    label: "Front-End",
    items: ["HTML", "CSS", "Bootstrap", "JavaScript", "TypeScript", "React", "AngularJS", "Angular 16", "Vue"],
  },
  {
    label: "Back-End",
    items: ["Node.js", "NestJS", "PHP", "Laravel", "Python", "FastAPI", "APIs REST"],
  },
  {
    label: "Banco de Dados",
    items: ["MySQL", "PostgreSQL", "SQL Server", "Modelagem de Dados"],
  },
  {
    label: "Análise & BI",
    items: ["UML", "Modelagem de Sistemas", "Design de BD", "Power BI"],
  },
  {
    label: "Ferramentas",
    items: ["Git", "GitHub", "Docker", "QGIS", "Scrum/Kanban"],
  },
];
</script>

<template>
  <section id="skills">
    <div class="container">
      <h2 class="section-heading">Skills</h2>
      <div class="skills">
        <div v-for="g in groups" :key="g.label" class="skills__group">
          <h3 class="mono skills__label">{{ g.label }}</h3>
          <div class="skills__items">
            <span v-for="i in g.items" :key="i" class="tag">{{ i }}</span>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.skills {
  display: flex;
  flex-direction: column;
  gap: 26px;
}

.skills__group {
  display: grid;
  grid-template-columns: 180px 1fr;
  gap: 20px;
  align-items: start;
}

.skills__label {
  color: var(--accent);
  padding-top: 6px;
}

.skills__items {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
}

@media (max-width: 640px) {
  .skills__group {
    grid-template-columns: 1fr;
    gap: 8px;
  }
}
</style>
