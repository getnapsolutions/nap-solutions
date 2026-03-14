<template>
  <section id="cost" class="section bg-alt">
    <div class="section-eyebrow">Revenue Impact</div>
    <h2 class="grad-text">What Silence Is<br />Costing You.</h2>
    <p class="section-sub">
      Conservative monthly estimate for a mid-size business:
    </p>
    <div class="cost-row">
      <div class="cost-cell">
        <div class="cost-big">4</div>
        <div class="cost-lbl">Missed calls<br />per night</div>
      </div>
      <div class="cost-op">&times;</div>
      <div class="cost-cell">
        <div class="cost-big">30</div>
        <div class="cost-lbl">Nights<br />per month</div>
      </div>
      <div class="cost-op">&times;</div>
      <div class="cost-cell">
        <div class="cost-big">$250</div>
        <div class="cost-lbl">Avg booking<br />value</div>
      </div>
      <div class="cost-op">=</div>
      <div class="cost-cell cost-cell-highlight">
        <div class="cost-big cost-big-highlight">$30K</div>
        <div class="cost-lbl">Lost revenue<br />per month</div>
      </div>
    </div>
    <p class="cost-note">
      That's up to <strong>$30,000+ in walkaway revenue</strong> every single
      month. NAP Solutions captures it back.
    </p>
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
.cost-row {
  display: flex;
  align-items: stretch;
  border-radius: 16px;
  overflow: hidden;
  border: 1px solid rgba(10,15,30,0.08);
  margin: 48px 0 32px;
  background: #fff;
  box-shadow: 0 4px 30px rgba(0,0,0,0.06);
}
.cost-cell {
  flex: 1;
  padding: 38px 28px;
  text-align: center;
  border-right: 1px solid rgba(10,15,30,0.08);
  border-left: 1px solid rgba(10,15,30,0.08);
}
.cost-cell-highlight {
  background: linear-gradient(135deg, rgba(123,47,255,0.04), rgba(0,212,192,0.04));
}
.cost-big {
  font-family: 'Orbitron', sans-serif;
  font-size: 38px;
  font-weight: 900;
  color: #7B2FFF;
  margin-bottom: 10px;
  line-height: 1;
}
.cost-big-highlight {
  font-size: 46px;
  background: linear-gradient(135deg, #7B2FFF, #00D4C0);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}
.cost-lbl {
  font-size: 15px;
  color: #8892b0;
  letter-spacing: 1px;
  line-height: 1.6;
}
.cost-op {
  font-family: 'Orbitron', sans-serif;
  font-size: 26px;
  font-weight: 900;
  color: rgba(123,47,255,0.2);
  display: flex;
  align-items: center;
  padding: 0 4px;
}
.cost-note {
  font-size: 18px;
  color: #4a5580;
  line-height: 1.8;
}
.cost-note strong {
  color: #7B2FFF;
  font-weight: 700;
}

@media (max-width: 960px) {
  .section {
    padding-left: 24px;
    padding-right: 24px;
  }
  .cost-row {
    flex-direction: column;
  }
  .cost-op {
    padding: 10px 0;
    justify-content: center;
  }
}
</style>
