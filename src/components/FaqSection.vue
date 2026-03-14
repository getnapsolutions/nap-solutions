<script setup>
import { ref, computed, onMounted } from 'vue'
import { faqCategories, faqItems } from '../data/faqData'

defineEmits(['open-booking'])

const searchQuery = ref('')
const activeTab = ref('general')
const openIndex = ref(-1)

function setTab(key) {
  activeTab.value = key
  openIndex.value = -1
}

function toggleItem(i) {
  openIndex.value = openIndex.value === i ? -1 : i
}

const filteredItems = computed(() => {
  const q = searchQuery.value.toLowerCase().trim()
  const isSearching = q !== ''

  return faqItems.map((item, i) => {
    const catMatch =
      isSearching || activeTab.value === 'all' || item.cat === activeTab.value
    const searchMatch =
      !isSearching ||
      item.q.toLowerCase().includes(q) ||
      item.a.toLowerCase().includes(q)
    return { ...item, originalIndex: i, visible: catMatch && searchMatch }
  })
})

const visibleItems = computed(() =>
  filteredItems.value.filter((item) => item.visible)
)

const noResults = computed(() => visibleItems.value.length === 0)
</script>

<template>
  <section id="faq" class="section bg-alt">
    <div class="section-eyebrow">FAQ</div>
    <h2 class="grad-text">Got Questions?<br />We've Got Answers.</h2>
    <p class="section-sub">
      Everything you need to know about NAP Solutions — find your answer
      instantly below.
    </p>

    <div class="faq-search-wrap">
      <input
        v-model="searchQuery"
        class="faq-search"
        type="text"
        placeholder="Search questions..."
        aria-label="Search FAQ questions"
      />
      <span class="faq-search-icon" aria-hidden="true">&#128269;</span>
    </div>

    <div class="faq-tabs" role="tablist">
      <button
        v-for="cat in faqCategories"
        :key="cat.key"
        class="faq-tab"
        :class="{ active: activeTab === cat.key }"
        role="tab"
        :aria-selected="activeTab === cat.key"
        @click="setTab(cat.key)"
      >
        {{ cat.label }}
      </button>
    </div>

    <div class="faq-list">
      <div
        v-for="item in filteredItems"
        :key="item.originalIndex"
        v-show="item.visible"
        class="faq-item"
        :class="{ open: openIndex === item.originalIndex }"
      >
        <button
          class="faq-q"
          :aria-expanded="openIndex === item.originalIndex"
          @click="toggleItem(item.originalIndex)"
        >
          {{ item.q }}
          <span class="faq-icon" aria-hidden="true">+</span>
        </button>
        <div class="faq-a">{{ item.a }}</div>
      </div>
    </div>

    <div v-if="noResults" class="no-results">
      No questions match your search. Try different keywords.
    </div>

    <div class="faq-cta">
      <div class="faq-cta-text">
        <h3>STILL HAVE QUESTIONS?</h3>
        <p>Book a free demo and we'll walk you through everything in person.</p>
      </div>
      <button class="btn-primary" @click="$emit('open-booking')">
        &#128197; Book a Demo
      </button>
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
.faq-search-wrap {
  max-width: 560px;
  margin-bottom: 48px;
  position: relative;
}
.faq-search {
  width: 100%;
  padding: 16px 50px 16px 22px;
  border: 1.5px solid rgba(10,15,30,0.08);
  border-radius: 12px;
  font-family: 'DM Sans', sans-serif;
  font-size: 17px;
  color: #0a0f1e;
  outline: none;
  background: #fff;
  box-shadow: 0 2px 12px rgba(0,0,0,0.05);
  transition: border-color 0.2s;
}
.faq-search:focus {
  border-color: rgba(123,47,255,0.4);
}
.faq-search-icon {
  position: absolute;
  right: 18px;
  top: 50%;
  transform: translateY(-50%);
  color: #8892b0;
  font-size: 18px;
  pointer-events: none;
}
.faq-tabs {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  margin-bottom: 44px;
}
.faq-tab {
  padding: 10px 22px;
  border-radius: 100px;
  border: 1.5px solid rgba(10,15,30,0.08);
  background: #fff;
  font-family: 'DM Sans', sans-serif;
  font-size: 15px;
  font-weight: 500;
  color: #4a5580;
  cursor: pointer;
  transition: all 0.2s;
}
.faq-tab:hover {
  border-color: rgba(123,47,255,0.3);
  color: #7B2FFF;
}
.faq-tab.active {
  background: linear-gradient(135deg, #7B2FFF, #00D4C0);
  border-color: transparent;
  color: #fff;
  font-weight: 700;
  box-shadow: 0 4px 14px rgba(123,47,255,0.25);
}
.faq-list {
  display: flex;
  flex-direction: column;
  gap: 12px;
  max-width: 860px;
}
.faq-item {
  background: #fff;
  border: 1.5px solid rgba(10,15,30,0.08);
  border-radius: 14px;
  overflow: hidden;
  transition: border-color 0.2s, box-shadow 0.2s;
}
.faq-item.open {
  border-color: rgba(123,47,255,0.25);
  box-shadow: 0 6px 24px rgba(123,47,255,0.08);
}
.faq-q {
  width: 100%;
  background: none;
  border: none;
  padding: 22px 26px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 20px;
  cursor: pointer;
  text-align: left;
  font-family: 'DM Sans', sans-serif;
  font-size: 17px;
  font-weight: 600;
  color: #0a0f1e;
  transition: color 0.2s;
}
.faq-item.open .faq-q {
  color: #7B2FFF;
}
.faq-icon {
  flex-shrink: 0;
  width: 30px;
  height: 30px;
  border-radius: 50%;
  background: #f5f7fb;
  border: 1px solid rgba(10,15,30,0.08);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 18px;
  color: #4a5580;
  transition: all 0.3s;
  font-weight: 300;
  line-height: 1;
}
.faq-item.open .faq-icon {
  background: linear-gradient(135deg, #7B2FFF, #00D4C0);
  border-color: transparent;
  color: #fff;
  transform: rotate(45deg);
}
.faq-a {
  max-height: 0;
  overflow: hidden;
  transition: max-height 0.35s ease, padding 0.3s ease;
  font-size: 16px;
  line-height: 1.8;
  color: #4a5580;
  padding: 0 26px;
}
.faq-item.open .faq-a {
  max-height: 300px;
  padding: 0 26px 22px;
}
.no-results {
  text-align: center;
  padding: 60px 20px;
  color: #8892b0;
  font-size: 17px;
}
.faq-cta {
  margin-top: 52px;
  padding: 40px 48px;
  background: linear-gradient(135deg, rgba(123,47,255,0.06), rgba(0,212,192,0.06));
  border: 1.5px solid rgba(123,47,255,0.15);
  border-radius: 20px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 24px;
  flex-wrap: wrap;
  max-width: 860px;
}
.faq-cta-text h3 {
  font-family: 'Orbitron', sans-serif;
  font-size: 18px;
  font-weight: 700;
  color: #0a0f1e;
  margin-bottom: 8px;
  letter-spacing: 1px;
}
.faq-cta-text p {
  font-size: 16px;
  color: #4a5580;
  line-height: 1.6;
}

@media (max-width: 960px) {
  .section {
    padding-left: 24px;
    padding-right: 24px;
  }
  .faq-cta {
    flex-direction: column;
    text-align: center;
  }
}
</style>
