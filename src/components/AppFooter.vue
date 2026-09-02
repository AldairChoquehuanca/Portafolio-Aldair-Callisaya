<script setup lang="ts">
const year = new Date().getFullYear();
</script>

<template>
  <footer class="footer">
    <div class="container footer__inner">
      <span class="mono">© {{ year }} Aldair Choquehuanca</span>
      <span class="mono">Feito com Vue.js</span>
    </div>
  </footer>
</template>

<style scoped>
.footer {
  padding: 32px 0;
}

.footer__inner {
  display: flex;
  justify-content: space-between;
  color: var(--text-muted);
}

@media (max-width: 480px) {
  .footer__inner {
    flex-direction: column;
    gap: 8px;
  }
}
</style>
