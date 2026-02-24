<template>
  <a href="#main-content" class="skip-link">Skip to main content</a>
  <NavBar />
  <main id="main-content" tabindex="-1">
    <HeroSection />
    <StatsSection />
    <FeaturesSection />
    <ScreenshotsSection />
    <HowItWorksSection />
    <IntegrationsSection />
    <CtaSection />
  </main>
  <FooterSection />
</template>
<style>
.skip-link {
  position: absolute;
  left: -999px;
  top: auto;
  width: 1px;
  height: 1px;
  overflow: hidden;
  z-index: 9999;
  background: #fff;
  color: #222;
  padding: 8px 16px;
  border-radius: 4px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.15);
}
.skip-link:focus {
  left: 16px;
  top: 16px;
  width: auto;
  height: auto;
  outline: 2px solid #6699ff;
}
</style>

<script setup>
import NavBar from "./components/NavBar.vue";
import HeroSection from "./components/HeroSection.vue";
import StatsSection from "./components/StatsSection.vue";
import FeaturesSection from "./components/FeaturesSection.vue";
import HowItWorksSection from "./components/HowItWorksSection.vue";
import ScreenshotsSection from "./components/ScreenshotsSection.vue";
import IntegrationsSection from "./components/IntegrationsSection.vue";
import CtaSection from "./components/CtaSection.vue";
import FooterSection from "./components/FooterSection.vue";
import { onMounted } from "vue";

onMounted(() => {
  // Add class first so the CSS hides elements, then immediately observe.
  // Elements already in the viewport fire synchronously on the first observe
  // call, so they become visible before the first paint.
  document.documentElement.classList.add("js-reveal");

  const observer = new IntersectionObserver(
    (entries) =>
      entries.forEach((e) => {
        if (e.isIntersecting) {
          e.target.classList.add("visible");
          observer.unobserve(e.target);
        }
      }),
    { threshold: 0 },
  );
  document.querySelectorAll(".reveal").forEach((el) => observer.observe(el));
});
</script>
