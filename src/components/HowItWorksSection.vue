<script setup>
import { functionCards } from '../data/howItWorksData'
</script>

<template>
  <section id="how" class="section bg-alt">
    <div class="section-eyebrow">How It Works</div>
    <h2 class="grad-text">
      From First Ring<br />To Fully Booked.
    </h2>
    <p class="section-sub">
      Every call handled end-to-end — here's exactly what our AI takes care
      of so you don't have to:
    </p>
    <div class="functions-grid">
      <div
        v-for="card in functionCards"
        :key="card.num"
        class="func-card"
      >
        <div class="func-num">{{ card.num }}</div>
        <h3>{{ card.title }}</h3>
        <p>{{ card.desc }}</p>
      </div>
      <div class="func-card filler">
        <div>
          <div class="filler-label">POWERED BY AI</div>
          <div class="filler-text">
            Natural voice.<br />Zero hold time.<br />24 / 7 availability.
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.section {
  padding: 72px 60px;
  position: relative;
}
.bg-alt {
  background: #f5f7fb;
}
.functions-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 18px;
  margin-top: 50px;
}
.func-card {
  padding: 30px 26px;
  border-radius: 16px;
  background: #fff;
  border: 1px solid rgba(10,15,30,0.08);
  box-shadow: 0 2px 16px rgba(0,0,0,0.04);
  transition: border-color 0.3s, transform 0.3s, box-shadow 0.3s;
  cursor: default;
}
.func-card:hover {
  border-color: rgba(123,47,255,0.25);
  transform: translateY(-4px);
  box-shadow: 0 12px 36px rgba(123,47,255,0.1);
}
.func-num {
  font-family: 'Orbitron', sans-serif;
  font-size: 13px;
  font-weight: 700;
  color: #00D4C0;
  letter-spacing: 2px;
  margin-bottom: 14px;
}
.func-card h3 {
  font-size: 17px;
  font-weight: 700;
  color: #0a0f1e;
  margin-bottom: 10px;
}
.func-card p {
  font-size: 15px;
  line-height: 1.8;
  color: #8892b0;
}
.func-card.filler {
  background: linear-gradient(135deg, rgba(123,47,255,0.04), rgba(0,212,192,0.04));
  border-color: rgba(123,47,255,0.1);
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
}
.filler-label {
  font-family: 'Orbitron', sans-serif;
  font-size: 11px;
  letter-spacing: 3px;
  color: #00D4C0;
  margin-bottom: 12px;
}
.filler-text {
  font-size: 14px;
  color: #8892b0;
  line-height: 2;
  letter-spacing: 1px;
}

@media (max-width: 960px) {
  .section {
    padding-left: 24px;
    padding-right: 24px;
  }
  .functions-grid {
    grid-template-columns: 1fr;
  }
}
</style>
