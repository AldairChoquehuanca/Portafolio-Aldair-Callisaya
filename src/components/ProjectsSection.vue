<script setup lang="ts">
import { reactive, ref, onMounted, onUnmounted } from "vue";

interface Project {
  name: string;
  year: string;
  description: string;
  stack: string[];
  images?: string[];
}

const projects: Project[] = [
  {
    name: "Praça Digital",
    year: "2024",
    description:
      "Reserva de espaços públicos com seleção de local/data/horário, upload de documentos e comprovante de pagamento. Painel administrativo completo com mapas interativos em QGIS.",
    stack: ["Laravel", "AngularJS", "QGIS", "Bootstrap"],
    images: ["/projects/praca1.jpg", "/projects/praca2.jpg", "/projects/praca3.jpg"],
  },
  {
    name: "Gestão de Almoxarifado",
    year: "2025",
    description:
      "Cadastro de materiais e fornecedores, controle de entradas/saídas e dashboard gerencial para a área de TI do Terminal de Ônibus de La Paz.",
    stack: ["Angular 16", "NestJS", "PostgreSQL"],
    images: ["/projects/almacen1.jpg", "/projects/almacen2.jpg"],
  },
  {
    name: "Biblioteca Virtual UTB",
    year: "2024",
    description:
      "Repositório acadêmico com painel administrativo Back-End para gestão de conteúdo e permissões, incluindo métricas de livros mais baixados.",
    stack: ["PHP", "Laravel", "JavaScript"],
    images: ["/projects/biblioteca.png"],
  },
  {
    name: "Repositório Acadêmico UTB",
    year: "2024",
    description:
      "Repositório de trabalhos acadêmicos da universidade, com painel administrativo para gestão de conteúdo, permissões de acesso e organização por curso e ano.",
    stack: ["PHP", "Laravel", "MySQL"],
    images: ["/projects/repositori.jpg"],
  },
  {
    name: "Sistema para Distribuidora de Bebidas",
    year: "2026",
    description:
      "Projeto freelance: controle operacional de vendas, compras, gestão de pessoal e dashboards para uma distribuidora.",
    stack: ["Full Stack", "Freelance"],
    // sin imagens: projeto privado de cliente
  },
];

// índice de la imagen activa por proyecto (para el carrusel dentro de la tarjeta)
const activeIndex = reactive<Record<string, number>>({});

function currentIndex(p: Project) {
  return activeIndex[p.name] ?? 0;
}

function currentImage(p: Project) {
  return p.images?.[currentIndex(p)] ?? "";
}

function nextImage(p: Project) {
  if (!p.images) return;
  activeIndex[p.name] = (currentIndex(p) + 1) % p.images.length;
}

function prevImage(p: Project) {
  if (!p.images) return;
  activeIndex[p.name] = (currentIndex(p) - 1 + p.images.length) % p.images.length;
}

function goToImage(p: Project, i: number) {
  activeIndex[p.name] = i;
}

// lightbox (imagen a pantalla completa)
const activeImage = ref<string | null>(null);

function openImage(src: string) {
  activeImage.value = src;
}

function closeImage() {
  activeImage.value = null;
}

function handleKeydown(e: KeyboardEvent) {
  if (e.key === "Escape") closeImage();
}

onMounted(() => window.addEventListener("keydown", handleKeydown));
onUnmounted(() => window.removeEventListener("keydown", handleKeydown));
</script>

<template>
  <section id="projetos">
    <div class="container">
      <h2 class="section-heading">Projetos</h2>
      <div class="projects">
        <article v-for="p in projects" :key="p.name" class="project">
          <div v-if="p.images && p.images.length" class="project__media">
            <button
              type="button"
              class="project__media-btn"
              @click="openImage(currentImage(p))"
            >
              <img
                :src="currentImage(p)"
                :alt="`Captura ${currentIndex(p) + 1} do projeto ${p.name}`"
                class="project__image"
              />
            </button>

            <template v-if="p.images.length > 1">
              <button type="button" class="project__nav project__nav--prev" @click.stop="prevImage(p)" aria-label="Imagem anterior">
                ‹
              </button>
              <button type="button" class="project__nav project__nav--next" @click.stop="nextImage(p)" aria-label="Próxima imagem">
                ›
              </button>
              <div class="project__dots">
                <button
                  v-for="(img, i) in p.images"
                  :key="img"
                  type="button"
                  class="project__dot"
                  :class="{ 'project__dot--active': i === currentIndex(p) }"
                  :aria-label="`Ver imagem ${i + 1}`"
                  @click.stop="goToImage(p, i)"
                />
              </div>
            </template>
          </div>

          <div class="project__head">
            <h3>{{ p.name }}</h3>
            <span class="mono project__year">{{ p.year }}</span>
          </div>
          <p>{{ p.description }}</p>
          <div class="project__stack">
            <span v-for="s in p.stack" :key="s" class="tag">{{ s }}</span>
          </div>
        </article>
      </div>
    </div>

    <div v-if="activeImage" class="lightbox" @click.self="closeImage">
      <button type="button" class="lightbox__close" @click="closeImage" aria-label="Fechar">
        ✕
      </button>
      <img :src="activeImage" class="lightbox__image" alt="" />
    </div>
  </section>
</template>

<style scoped>
.projects {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  align-items: start;
  gap: 20px;
}

.project {
  background: var(--bg);
  border: 1px solid var(--line);
  border-radius: var(--radius);
  padding: 20px;
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.project__media {
  position: relative;
  aspect-ratio: 16 / 9;
  border-radius: var(--radius);
  overflow: hidden;
  border: 1px solid var(--line);
  background: var(--surface);
}

.project__media-btn {
  display: block;
  width: 100%;
  height: 100%;
  padding: 0;
  border: none;
  background: none;
  cursor: pointer;
}

.project__image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
}

.project__nav {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  width: 30px;
  height: 30px;
  border-radius: 50%;
  border: 1px solid var(--line);
  background: rgba(10, 13, 18, 0.72);
  color: var(--text);
  font-size: 18px;
  line-height: 1;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
}

.project__nav--prev {
  left: 8px;
}

.project__nav--next {
  right: 8px;
}

.project__dots {
  position: absolute;
  bottom: 8px;
  left: 0;
  right: 0;
  display: flex;
  justify-content: center;
  gap: 6px;
}

.project__dot {
  width: 6px;
  height: 6px;
  border-radius: 50%;
  border: none;
  background: rgba(231, 234, 238, 0.4);
  padding: 0;
  cursor: pointer;
}

.project__dot--active {
  background: var(--accent);
}

.project__head {
  display: flex;
  align-items: baseline;
  justify-content: space-between;
  gap: 12px;
}

.project__head h3 {
  font-size: 17px;
}

.project__year {
  color: var(--text-muted);
  white-space: nowrap;
}

.project p {
  font-size: 14.5px;
}

.project__stack {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-top: auto;
  padding-top: 4px;
}

.lightbox {
  position: fixed;
  inset: 0;
  background: rgba(8, 10, 14, 0.9);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 50;
  padding: 32px;
}

.lightbox__image {
  max-width: 100%;
  max-height: 100%;
  border-radius: var(--radius);
  border: 1px solid var(--line);
}

.lightbox__close {
  position: absolute;
  top: 20px;
  right: 24px;
  background: var(--surface);
  border: 1px solid var(--line);
  color: var(--text);
  width: 36px;
  height: 36px;
  border-radius: var(--radius);
  cursor: pointer;
  font-size: 16px;
}
</style>