<template>
  <NavBar />
  <main>
    <HeroSection />
    <StatsSection />
    <FeaturesSection />
    <HowItWorksSection />
    <IntegrationsSection />
    <CtaSection />
  </main>
  <FooterSection />
</template>

<script setup>
import NavBar from './components/NavBar.vue'
import HeroSection from './components/HeroSection.vue'
import StatsSection from './components/StatsSection.vue'
import FeaturesSection from './components/FeaturesSection.vue'
import HowItWorksSection from './components/HowItWorksSection.vue'
import IntegrationsSection from './components/IntegrationsSection.vue'
import CtaSection from './components/CtaSection.vue'
import FooterSection from './components/FooterSection.vue'
import { onMounted } from 'vue'

onMounted(() => {
  // Add class first so the CSS hides elements, then immediately observe.
  // Elements already in the viewport fire synchronously on the first observe
  // call, so they become visible before the first paint.
  document.documentElement.classList.add('js-reveal')

  const observer = new IntersectionObserver(
    (entries) => entries.forEach(e => {
      if (e.isIntersecting) {
        e.target.classList.add('visible')
        observer.unobserve(e.target)
      }
    }),
    { threshold: 0 }
  )
  document.querySelectorAll('.reveal').forEach(el => observer.observe(el))
})
</script>
