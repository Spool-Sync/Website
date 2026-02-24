<template>
  <section
    id="features"
    class="features-section"
    aria-labelledby="features-title"
  >
    <div class="container">
      <div class="section-header reveal">
        <p class="section-label">Features</p>
        <h2 id="features-title" class="section-title">
          Everything your filament<br />inventory needs
        </h2>
        <p class="section-subtitle">
          From the scale to the screen — SpoolSync connects your hardware to a
          unified dashboard that keeps you informed and in control.
        </p>
      </div>

      <div class="features-grid">
        <FeatureCard
          v-for="(f, i) in features"
          :key="f.title"
          v-bind="f"
          :delay="(i % 3) + 1"
        />
      </div>
    </div>
  </section>
</template>

<script setup>
import FeatureCard from "./FeatureCard.vue";

const features = [
  {
    icon: `<svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"><path d="M12 2L2 7l10 5 10-5-10-5z"/><path d="M2 17l10 5 10-5"/><path d="M2 12l10 5 10-5"/></svg>`,
    title: "Live Weight Tracking",
    description:
      "ESP32-based load cells report spool weights in real time over Wi-Fi. Watch the number update as your printer consumes filament.",
    accent: "#6699ff",
  },
  {
    icon: `<svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"><rect x="2" y="5" width="20" height="14" rx="2"/><path d="M2 10h20"/></svg>`,
    title: "NFC Tag Scanning",
    description:
      "Tap a spool with your phone to instantly pull up its details or kick off the ingest flow. Supports OpenPrintTag, Bambu, and plain serial tags.",
    accent: "#9966ff",
  },
  {
    icon: `<svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M12 8v4l3 3"/></svg>`,
    title: "Printer Integration",
    description:
      "Poll PrusaLink and PrusaConnect for live print job status. Automatically deduct filament when a job completes.",
    accent: "#ff6b9d",
  },
  {
    icon: `<svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"><path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0118 0z"/><circle cx="12" cy="10" r="3"/></svg>`,
    title: "Storage Locations",
    description:
      "Organise spools into drying chambers, long-term storage, and open shelves. Know exactly where every spool is at a glance.",
    accent: "#51cf66",
  },
  {
    icon: `<svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"><path d="M18 20V10M12 20V4M6 20v-6"/></svg>`,
    title: "Smart Inventory Alerts",
    description:
      "Set per-filament reorder thresholds. SpoolSync notifies you the moment a spool drops below the minimum, so you can reorder before it runs dry.",
    accent: "#ffd43b",
  },
  {
    icon: `<svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"><path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"/></svg>`,
    title: "Self-Hosted & Private",
    description:
      "Deploy with a single Docker Compose command. Your filament data stays on your server — no subscriptions, no cloud lock-in, no telemetry.",
    accent: "#ff9f43",
  },
  {
    icon: `<svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"><path d="M17 21v-2a4 4 0 00-4-4H5a4 4 0 00-4 4v2"/><circle cx="9" cy="7" r="4"/><path d="M23 21v-2a4 4 0 00-3-3.87"/><path d="M16 3.13a4 4 0 010 7.75"/></svg>`,
    title: "Role-Based Access Control",
    description:
      "Create custom roles with per-resource permissions across 10 groups. Grant team members exactly the access they need — view-only, editor, or full admin.",
    accent: "#4dabf7",
  },
  {
    icon: `<svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="11" width="18" height="11" rx="2"/><path d="M7 11V7a5 5 0 0110 0v4"/><circle cx="12" cy="16" r="1" fill="currentColor"/></svg>`,
    title: "Single Sign-On",
    description:
      "Log in with any OIDC-compatible provider — Authentik, Keycloak, Entra ID, and more. SSO groups are automatically mapped to SpoolSync roles on every login.",
    accent: "#cc5de8",
  },
];
</script>

<style scoped>
.features-section {
  padding: 120px 0 80px;
}

.section-header {
  margin-bottom: 64px;
}

.features-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 20px;
}

@media (max-width: 1100px) {
  .features-grid {
    grid-template-columns: repeat(3, 1fr);
  }
}

@media (max-width: 900px) {
  .features-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 580px) {
  .features-grid {
    grid-template-columns: 1fr;
  }
  .features-section {
    padding: 80px 0 60px;
  }
}
</style>
