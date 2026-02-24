<template>
  <footer class="footer" role="contentinfo" aria-label="Footer">
    <div class="container footer-inner">
      <div class="footer-brand">
        <a href="#" class="footer-logo" aria-label="SpoolSync Home">
          <img
            src="/logo.svg"
            width="28"
            height="28"
            alt="SpoolSync logo"
            class="footer-logo-img"
            loading="lazy"
          />
          SpoolSync
        </a>
        <p class="footer-tagline">
          Open-source filament management<br />for serious 3D printing setups.
        </p>
      </div>

      <div class="footer-links">
        <div class="footer-col">
          <div class="footer-col-title">Product</div>
          <a href="#features">Features</a>
          <a href="#how-it-works">How it works</a>
          <a href="#integrations">Integrations</a>
          <a href="#get-started">Get Started</a>
        </div>

        <div class="footer-col">
          <div class="footer-col-title">Resources</div>
          <a
            href="https://github.com/Spool-Sync/SpoolSync-App"
            target="_blank"
            rel="noopener"
            >GitHub</a
          >
          <a
            href="https://github.com/Spool-Sync/SpoolSync-App/issues"
            target="_blank"
            rel="noopener"
            >Report Issue</a
          >
          <a
            href="https://github.com/Spool-Sync/SpoolSync-App/releases"
            target="_blank"
            rel="noopener"
            >Releases</a
          >
          <a
            href="https://github.com/Spool-Sync/SpoolSync-App/blob/main/LICENSE"
            target="_blank"
            rel="noopener"
            >License</a
          >
        </div>

        <div class="footer-col">
          <div class="footer-col-title">Tech Stack</div>
          <a href="https://vuejs.org" target="_blank" rel="noopener">Vue 3</a>
          <a href="https://www.prisma.io" target="_blank" rel="noopener"
            >Prisma</a
          >
          <a href="https://expressjs.com" target="_blank" rel="noopener"
            >Express</a
          >
          <a href="https://socket.io" target="_blank" rel="noopener"
            >Socket.IO</a
          >
        </div>
      </div>
    </div>

    <div class="footer-bottom">
      <div class="container footer-bottom-inner">
        <span>SpoolSync — Open Source under GPL-3.0 License</span>
        <span>Built for makers, by makers</span>
      </div>
    </div>
  </footer>
</template>

<style scoped>
.footer {
  border-top: 1px solid var(--border);
  background: var(--surface);
}

.footer-inner {
  display: grid;
  grid-template-columns: 1.4fr 1fr;
  gap: 60px;
  padding-top: 64px;
  padding-bottom: 64px;
  align-items: start;
}

.footer-logo {
  display: flex;
  align-items: center;
  gap: 9px;
  font-size: 16px;
  font-weight: 700;
  color: var(--text);
  letter-spacing: -0.02em;
  margin-bottom: 14px;
}
.footer-logo:hover {
  color: var(--primary);
}
.footer-logo-img {
  filter: brightness(0) invert(1);
}

.footer-tagline {
  font-size: 13px;
  line-height: 1.7;
  color: var(--text-muted);
}

.footer-links {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 32px;
}

.footer-col {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.footer-col-title {
  font-size: 11px;
  font-weight: 700;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: var(--text);
  margin-bottom: 4px;
}

.footer-col a {
  font-size: 13px;
  color: var(--text-muted);
  transition: color 0.2s;
}
.footer-col a:hover {
  color: var(--text);
}

.footer-bottom {
  border-top: 1px solid var(--border-dim);
  padding: 18px 0;
}

.footer-bottom-inner {
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-size: 12px;
  color: var(--text-dim);
}

@media (max-width: 860px) {
  .footer-inner {
    grid-template-columns: 1fr;
    gap: 40px;
  }
  .footer-bottom-inner {
    flex-direction: column;
    gap: 6px;
    text-align: center;
  }
}

@media (max-width: 520px) {
  .footer-links {
    grid-template-columns: 1fr 1fr;
  }
}
</style>
