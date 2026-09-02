<script setup lang="ts">
const contacts = [
  { label: "Email", value: "callisayaaldair@gmail.com", href: "mailto:callisayaaldair@gmail.com" },
  {
    label: "LinkedIn",
    value: "aldair-kelvin-choquehuanca",
    href: "https://linkedin.com/in/aldair-kelvin-choquehuanca-callisaya-5014033a3",
  },
  { label: "Localização", value: "São Paulo, SP, Brasil", href: null },
];
</script>

<template>
  <section id="contato">
    <div class="container contact">
      <div>
        <h2 class="section-heading">Contato</h2>
        <p class="contact__text">
          Aberto a oportunidades como
          Desenvolvedor Full Stack, Software Engineer ou Front-End/Back-End.
        </p>
      </div>
      <ul class="contact__list">
        <li v-for="c in contacts" :key="c.label">
          <span class="mono contact__label">{{ c.label }}</span>
          <a v-if="c.href" :href="c.href" target="_blank" rel="noopener">{{ c.value }}</a>
          <span v-else>{{ c.value }}</span>
        </li>
      </ul>
    </div>
  </section>
</template>

<style scoped>
.contact {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 48px;
  align-items: start;
}

.contact__text {
  font-size: 15.5px;
}

.contact__list {
  list-style: none;
  margin: 0;
  padding: 0;
  display: flex;
  flex-direction: column;
  gap: 16px;
}

.contact__list li {
  display: flex;
  justify-content: space-between;
  align-items: baseline;
  border-bottom: 1px solid var(--line);
  padding-bottom: 14px;
  font-size: 15px;
}

.contact__list a {
  text-decoration: none;
  color: var(--accent);
}

.contact__list a:hover {
  text-decoration: underline;
}

.contact__label {
  color: var(--text-muted);
}

@media (max-width: 640px) {
  .contact {
    grid-template-columns: 1fr;
    gap: 24px;
  }
}
</style>
