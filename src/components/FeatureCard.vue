<template>
  <div :class="['feature-card', 'reveal', `reveal-delay-${delay}`]">
    <div class="feature-icon" :style="{ color: accent, background: `${accent}14`, boxShadow: `0 0 0 1px ${accent}22` }">
      <span v-html="icon"></span>
    </div>
    <h3 class="feature-title">{{ title }}</h3>
    <p class="feature-desc">{{ description }}</p>
    <div class="feature-line" :style="{ background: `linear-gradient(90deg, ${accent} 0%, transparent 100%)` }"></div>
  </div>
</template>

<script setup>
defineProps({
  icon:        { type: String, required: true },
  title:       { type: String, required: true },
  description: { type: String, required: true },
  accent:      { type: String, default: '#6699ff' },
  delay:       { type: Number, default: 1 },
})
</script>

<style scoped>
.feature-card {
  background: var(--card);
  border: 1px solid var(--border);
  border-radius: var(--radius-lg);
  padding: 28px;
  position: relative;
  overflow: hidden;
  transition: border-color 0.25s, transform 0.25s, box-shadow 0.25s;
  cursor: default;
}

.feature-card:hover {
  border-color: rgba(102, 153, 255, 0.3);
  transform: translateY(-3px);
  box-shadow: 0 12px 40px rgba(0, 0, 0, 0.4), var(--glow);
}

.feature-icon {
  width: 44px;
  height: 44px;
  border-radius: var(--radius-sm);
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 20px;
  flex-shrink: 0;
}

.feature-title {
  font-size: 16px;
  font-weight: 700;
  color: var(--text);
  margin-bottom: 10px;
  letter-spacing: -0.01em;
}

.feature-desc {
  font-size: 14px;
  line-height: 1.65;
  color: var(--text-muted);
}

.feature-line {
  position: absolute;
  bottom: 0;
  left: 0;
  height: 2px;
  width: 100%;
  opacity: 0;
  transition: opacity 0.25s;
}

.feature-card:hover .feature-line { opacity: 1; }
</style>
