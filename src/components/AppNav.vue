<script setup lang="ts">
const links = [
  { href: "#sobre", label: "Sobre" },
  { href: "#experiencia", label: "Experiência" },
  { href: "#projetos", label: "Projetos" },
  { href: "#skills", label: "Skills" },
  { href: "#contato", label: "Contato" },
];
</script>

<template>
  <header class="nav">
    <div class="container nav__inner">
      <a href="#top" class="nav__brand">Aldair Choquehuanca</a>
      <nav class="nav__links">
        <a v-for="l in links" :key="l.href" :href="l.href">{{ l.label }}</a>
      </nav>
    </div>
  </header>
</template>

<style scoped>
.nav {
  position: sticky;
  top: 0;
  z-index: 10;
  background: rgba(16, 20, 26, 0.85);
  backdrop-filter: blur(8px);
  border-bottom: 1px solid var(--line);
}

.nav__inner {
  display: flex;
  align-items: center;
  justify-content: space-between;
  height: 64px;
  gap: 16px;
}

.nav__brand {
  font-family: var(--font-display);
  font-size: 15px;
  font-weight: 600;
  text-decoration: none;
  color: var(--text);
  white-space: nowrap;
  flex-shrink: 0;
}

.nav__links {
  display: flex;
  gap: 28px;
  overflow-x: auto;
  scrollbar-width: none;
  -ms-overflow-style: none;
}

.nav__links::-webkit-scrollbar {
  display: none;
}

.nav__links a {
  font-size: 14px;
  text-decoration: none;
  color: var(--text-muted);
  transition: color 0.15s ease;
  white-space: nowrap;
}

.nav__links a:hover {
  color: var(--accent);
}

@media (max-width: 640px) {
  .nav__inner {
    height: 56px;
    justify-content: center;
  }

  .nav__brand {
    display: none;
  }

  .nav__links {
    gap: 18px;
    width: 100%;
    justify-content: flex-start;
    padding: 0 4px;
  }

  .nav__links a {
    font-size: 13px;
  }
}
</style>