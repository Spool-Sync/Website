<template>
  <header :class="['navbar', { scrolled }]" role="banner">
    <div class="container nav-inner">
      <a href="#" class="nav-logo" aria-label="SpoolSync Home">
        <img
          src="/logo.svg"
          width="32"
          height="32"
          alt="SpoolSync logo"
          class="nav-logo-img"
          loading="lazy"
        />
        <span>SpoolSync</span>
      </a>

      <nav class="nav-links" role="navigation" aria-label="Main navigation">
        <a href="#features">Features</a>
        <a href="#how-it-works">How it works</a>
        <a href="#integrations">Integrations</a>
        <a
          href="https://github.com/Spool-Sync/SpoolSync-App"
          target="_blank"
          rel="noopener"
          aria-label="GitHub repository"
          >GitHub</a
        >
      </nav>

      <a
        href="#get-started"
        class="btn btn-primary nav-cta"
        aria-label="Get Started"
        >Get Started</a
      >

      <button
        class="nav-mobile-toggle"
        @click="mobileOpen = !mobileOpen"
        aria-label="Toggle menu"
        aria-controls="nav-mobile"
        aria-expanded="mobileOpen"
      >
        <span :class="{ active: mobileOpen }"></span>
        <span :class="{ active: mobileOpen }"></span>
        <span :class="{ active: mobileOpen }"></span>
      </button>
    </div>

    <div
      :class="['nav-mobile', { open: mobileOpen }]"
      id="nav-mobile"
      role="navigation"
      aria-label="Mobile navigation"
    >
      <a href="#features" @click="mobileOpen = false">Features</a>
      <a href="#how-it-works" @click="mobileOpen = false">How it works</a>
      <a href="#integrations" @click="mobileOpen = false">Integrations</a>
      <a
        href="https://github.com/Spool-Sync/SpoolSync-App"
        target="_blank"
        rel="noopener"
        aria-label="GitHub repository"
        >GitHub</a
      >
      <a
        href="#get-started"
        class="btn btn-primary"
        style="text-align: center"
        @click="mobileOpen = false"
        aria-label="Get Started"
        >Get Started</a
      >
    </div>
  </header>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from "vue";

const scrolled = ref(false);
const mobileOpen = ref(false);

function onScroll() {
  scrolled.value = window.scrollY > 40;
}
onMounted(() => window.addEventListener("scroll", onScroll));
onUnmounted(() => window.removeEventListener("scroll", onScroll));
</script>

<style scoped>
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 100;
  transition:
    background 0.3s,
    border-color 0.3s,
    backdrop-filter 0.3s;
  border-bottom: 1px solid transparent;
}

.navbar.scrolled {
  background: rgba(8, 9, 14, 0.85);
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
  border-bottom-color: var(--border);
}

.nav-inner {
  display: flex;
  align-items: center;
  height: 68px;
  gap: 40px;
}

.nav-logo {
  display: flex;
  align-items: center;
  gap: 10px;
  font-size: 17px;
  font-weight: 700;
  letter-spacing: -0.02em;
  color: var(--text);
  flex-shrink: 0;
}

.nav-logo:hover {
  color: var(--primary);
}
.nav-logo span {
  transition: color 0.2s;
}
.nav-logo-img {
  filter: brightness(0) invert(1);
}

.nav-links {
  display: flex;
  align-items: center;
  gap: 32px;
  flex: 1;
}

.nav-links a {
  font-size: 14px;
  font-weight: 500;
  color: var(--text-muted);
  transition: color 0.2s;
}
.nav-links a:hover {
  color: var(--text);
}

.nav-cta {
  margin-left: auto;
  padding: 10px 20px;
  font-size: 13px;
}

.nav-mobile-toggle {
  display: none;
  flex-direction: column;
  gap: 5px;
  background: none;
  border: none;
  cursor: pointer;
  padding: 4px;
  margin-left: auto;
}

.nav-mobile-toggle span {
  display: block;
  width: 22px;
  height: 2px;
  background: var(--text-muted);
  border-radius: 1px;
  transition: all 0.25s;
}

.nav-mobile {
  display: none;
  flex-direction: column;
  gap: 4px;
  padding: 12px 24px 20px;
  background: var(--surface);
  border-top: 1px solid var(--border);
}

.nav-mobile.open {
  display: flex;
}

.nav-mobile a {
  font-size: 15px;
  font-weight: 500;
  color: var(--text-muted);
  padding: 10px 4px;
  border-bottom: 1px solid var(--border-dim);
  transition: color 0.2s;
}
.nav-mobile a:hover {
  color: var(--text);
}
.nav-mobile a:last-child {
  border: none;
  margin-top: 8px;
}

@media (max-width: 768px) {
  .nav-links,
  .nav-cta {
    display: none;
  }
  .nav-mobile-toggle {
    display: flex;
  }
}
</style>
