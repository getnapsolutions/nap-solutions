<script setup>
import logoImg from '../assets/logo.png'

defineEmits(['open-booking'])
</script>

<template>
  <nav class="nav">
    <a class="nav-logo" href="#">
      <img :src="logoImg" alt="NAP Solutions" class="nav-logo-img" />
      <span class="nav-wordmark">NAP SOLUTIONS</span>
    </a>
    <ul class="nav-links">
      <li><a href="#problem">The Problem</a></li>
      <li><a href="#solution">The Solution</a></li>
      <li><a href="#how">How It Works</a></li>
      <li><a href="#pricing">Pricing</a></li>
      <li><a href="#faq">FAQ</a></li>
      <li>
        <a
          href="#"
          class="nav-cta"
          @click.prevent="$emit('open-booking')"
        >
          Book a Demo
        </a>
      </li>
    </ul>
  </nav>
</template>

<style scoped>
.nav {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 100;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 18px 60px;
  background: rgba(255, 255, 255, 0.92);
  backdrop-filter: blur(24px);
  border-bottom: 1px solid rgba(10, 15, 30, 0.08);
  box-shadow: 0 1px 20px rgba(0, 0, 0, 0.06);
}
.nav-logo {
  display: flex;
  align-items: center;
  gap: 12px;
  text-decoration: none;
}
.nav-logo-img {
  width: 40px;
  height: 40px;
  border-radius: 10px;
  object-fit: cover;
}
.nav-wordmark {
  font-family: 'Orbitron', sans-serif;
  font-weight: 900;
  font-size: 17px;
  letter-spacing: 5px;
  background: linear-gradient(90deg, #0a0f1e 0%, #7B2FFF 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}
.nav-links {
  display: flex;
  align-items: center;
  gap: 34px;
  list-style: none;
}
.nav-links a {
  color: #4a5580;
  text-decoration: none;
  font-size: 16px;
  font-weight: 500;
  transition: color 0.2s;
}
.nav-links a:hover {
  color: #0a0f1e;
}
.nav-cta {
  background: linear-gradient(135deg, #7B2FFF, #00D4C0) !important;
  color: #fff !important;
  padding: 11px 26px;
  border-radius: 9px;
  font-weight: 700 !important;
  font-size: 16px !important;
  box-shadow: 0 4px 15px rgba(123, 47, 255, 0.3);
  transition: all 0.2s !important;
}
.nav-cta:hover {
  opacity: 0.9;
  transform: translateY(-1px);
  box-shadow: 0 6px 20px rgba(123, 47, 255, 0.4) !important;
}

@media (max-width: 960px) {
  .nav {
    padding: 14px 24px;
  }
  .nav-links {
    display: none;
  }
}
</style>
