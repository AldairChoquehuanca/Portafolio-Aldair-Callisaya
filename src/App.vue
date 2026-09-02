<script setup lang="ts">
import AppNav from "./components/AppNav.vue";
import HeroSection from "./components/HeroSection.vue";
import AboutSection from "./components/AboutSection.vue";
import ExperienceSection from "./components/ExperienceSection.vue";
import ProjectsSection from "./components/ProjectsSection.vue";
import SkillsSection from "./components/SkillsSection.vue";
import EducationSection from "./components/EducationSection.vue";
import ContactSection from "./components/ContactSection.vue";
import AppFooter from "./components/AppFooter.vue";
</script>

<template>
  <AppNav />
  <main>
    <HeroSection />
    <AboutSection />
    <ExperienceSection />
    <ProjectsSection />
    <SkillsSection />
    <EducationSection />
    <ContactSection />
  </main>
  <AppFooter />
</template>
