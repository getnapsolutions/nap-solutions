<template>
  <div class="marquee-wrap">
    <div class="marquee-track">
      <span v-for="i in 16" :key="i" class="marquee-item">
        BOOK <span class="marquee-sep">&middot;</span>
        ANSWER <span class="marquee-sep">&middot;</span>
        AUTOMATE
      </span>
    </div>
  </div>
</template>

<style scoped>
.marquee-wrap {
  overflow: hidden;
  border-top: 1px solid rgba(10,15,30,0.08);
  border-bottom: 1px solid rgba(10,15,30,0.08);
  background: #f5f7fb;
  padding: 16px 0;
}
.marquee-track {
  display: flex;
  width: max-content;
  animation: marquee 25s linear infinite;
}
.marquee-item {
  font-size: 12px;
  letter-spacing: 5px;
  color: #8892b0;
  padding: 0 32px;
  white-space: nowrap;
  font-family: 'Space Mono', monospace;
}
.marquee-sep {
  color: #00D4C0;
}
</style>
