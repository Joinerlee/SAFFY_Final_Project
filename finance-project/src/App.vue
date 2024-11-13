<!-- App.vue -->
<template>
  <div class="app">
    <!-- Header -->
    <header class="header">
      <div class="container header-container">
        <router-link to="/" class="logo">
          Juuk Juuk
        </router-link>
        <nav class="main-nav">
          <router-link
            v-for="item in menuItems"
            :key="item"
            :to="''"
            class="nav-link"
          >
            {{ item }}
          </router-link>
        </nav>
        <button class="login-button">
          로그인
        </button>
      </div>
    </header>

    <!-- Hero Section -->
    <section class="hero">
      <div class="container">
        <div
          v-motion
          :initial="{ opacity: 0, y: 20 }"
          :enter="{ opacity: 1, y: 0 }"
          class="hero-content"
        >
          <h1 class="hero-title">
            스마트한 금융의 미래,<br />지금 시작하세요
          </h1>
          <p class="hero-description">
            Juuk Juuk과 함께 당신의 재무 목표를 달성하고 더 나은 금융 생활을 경험하세요
          </p>
          <button class="start-button">
            시작하기
            <chevron-right-icon class="chevron-icon" />
          </button>
        </div>
      </div>
    </section>

    <!-- Services Section -->
    <section class="services">
      <div class="container">
        <h2 class="section-title">
          스마트한 금융 서비스
        </h2>
        <div class="services-grid">
          <div
            v-for="(service, index) in services"
            :key="index"
            v-motion
            :initial="{ opacity: 0, y: 20 }"
            :enter="{ opacity: 1, y: 0, transition: { delay: index * 100 } }"
            class="service-card"
          >
            <component :is="service.icon" class="service-icon" />
            <h3 class="service-title">{{ service.title }}</h3>
            <p class="service-description">{{ service.description }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Products Section -->
    <section class="products">
      <div class="container">
        <h2 class="section-title">
          프리미엄 금융 상품
        </h2>
        <div class="products-grid">
          <div
            v-for="(product, index) in products"
            :key="index"
            v-motion
            :initial="{ opacity: 0, y: 20 }"
            :enter="{ opacity: 1, y: 0, transition: { delay: index * 100 } }"
            class="product-card"
          >
            <h3 class="product-title">
              {{ product.title }}
            </h3>
            <div class="rate-container">
              <p class="rate">{{ product.rate }}</p>
              <p class="rate-description">기본금리 (연)</p>
            </div>
            <p class="period">기간: 12개월</p>
            <button class="join-button">
              가입하기
            </button>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import { BarChart2Icon, RefreshCcwIcon, MapPinIcon, UsersIcon, ChevronRightIcon } from 'lucide-vue-next'

const menuItems = ['원율계산', '주변은행', '커뮤니티', '금융상품추천']

const services = [
  { title: "예적금 상품 조회", description: "최적의 금융 상품을 찾아 비교하세요", icon: BarChart2Icon },
  { title: "실시간 환율 계산기", description: "정확한 환율로 빠르게 계산해 드립니다", icon: RefreshCcwIcon },
  { title: "주변 은행 찾기", description: "가까운 은행과 ATM을 쉽게 찾아보세요", icon: MapPinIcon },
  { title: "금융 커뮤니티", description: "다양한 금융 정보와 경험을 공유하세요", icon: UsersIcon },
]

const products = [
  { title: "스마트 정기예금", rate: "3.6%" },
  { title: "프리미엄 정기예금", rate: "3.7%" },
  { title: "디지털 정기예금", rate: "3.8%" },
]
</script>

<style>
/* Reset & Base Styles */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

:root {
  --primary-color: #1d4ed8;
  --primary-hover: #1e40af;
  --text-dark: #111827;
  --text-light: #4b5563;
  --background-light: #f9fafb;
  --white: #ffffff;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 1rem;
}

/* Header Styles */
.header {
  background-color: var(--white);
  box-shadow: 0 1px 3px rgba(0,0,0,0.1);
  position: sticky;
  top: 0;
  z-index: 50;
}

.header-container {
  display: flex;
  height: 4rem;
  align-items: center;
  justify-content: space-between;
}

.logo {
  font-size: 1.5rem;
  font-weight: 700;
  color: var(--primary-color);
  text-decoration: none;
  transition: color 0.2s;
}

.logo:hover {
  color: var(--primary-hover);
}

.main-nav {
  display: none;
}

@media (min-width: 768px) {
  .main-nav {
    display: flex;
    gap: 0.25rem;
  }
}

.nav-link {
  padding: 0.5rem 0.75rem;
  border-radius: 0.375rem;
  font-size: 0.875rem;
  font-weight: 500;
  color: var(--text-light);
  text-decoration: none;
  transition: all 0.2s;
}

.nav-link:hover {
  color: var(--primary-color);
  background-color: #eff6ff;
}

.login-button {
  padding: 0.5rem 1rem;
  border: 1px solid var(--primary-color);
  border-radius: 0.375rem;
  font-size: 0.875rem;
  color: var(--primary-color);
  background: none;
  cursor: pointer;
  transition: all 0.2s;
}

.login-button:hover {
  background-color: #eff6ff;
}

/* Hero Section */
.hero {
  background-color: var(--white);
  padding: 6rem 0;
}

.hero-content {
  max-width: 48rem;
  margin: 0 auto;
  text-align: center;
}

.hero-title {
  margin-bottom: 1.5rem;
  font-size: 2.25rem;
  font-weight: 700;
  color: var(--text-dark);
  line-height: 1.2;
}

@media (min-width: 640px) {
  .hero-title {
    font-size: 3rem;
  }
}

.hero-description {
  margin-bottom: 2.5rem;
  font-size: 1.25rem;
  color: var(--text-light);
}

.start-button {
  padding: 0.75rem 2rem;
  border: none;
  border-radius: 0.375rem;
  background-color: var(--primary-color);
  color: var(--white);
  font-size: 1.125rem;
  font-weight: 600;
  cursor: pointer;
  transition: background-color 0.2s;
  display: inline-flex;
  align-items: center;
}

.start-button:hover {
  background-color: var(--primary-hover);
}

.chevron-icon {
  width: 1.25rem;
  height: 1.25rem;
  margin-left: 0.5rem;
}

/* Services Section */
.services {
  padding: 6rem 0;
  background-color: var(--background-light);
}

.section-title {
  margin-bottom: 4rem;
  text-align: center;
  font-size: 1.875rem;
  font-weight: 700;
  color: var(--text-dark);
}

.services-grid {
  display: grid;
  gap: 2rem;
  grid-template-columns: 1fr;
}

@media (min-width: 768px) {
  .services-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (min-width: 1024px) {
  .services-grid {
    grid-template-columns: repeat(4, 1fr);
  }
}

.service-card {
  padding: 1.5rem;
  background-color: var(--white);
  border-radius: 0.5rem;
  box-shadow: 0 1px 3px rgba(0,0,0,0.1);
  transition: box-shadow 0.2s;
}

.service-card:hover {
  box-shadow: 0 4px 6px rgba(0,0,0,0.1);
}

.service-icon {
  width: 2.5rem;
  height: 2.5rem;
  margin-bottom: 1rem;
  color: var(--primary-color);
}

.service-title {
  margin-bottom: 0.75rem;
  font-size: 1.25rem;
  font-weight: 600;
  color: var(--text-dark);
}

.service-description {
  color: var(--text-light);
}

/* Products Section */
.products {
  padding: 6rem 0;
  background-color: var(--white);
}

.products-grid {
  display: grid;
  gap: 2rem;
  grid-template-columns: 1fr;
}

@media (min-width: 768px) {
  .products-grid {
    grid-template-columns: repeat(3, 1fr);
  }
}

.product-card {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 2rem;
  background-color: var(--background-light);
  border-radius: 0.5rem;
  box-shadow: 0 1px 3px rgba(0,0,0,0.1);
  transition: all 0.2s;
}

.product-card:hover {
  box-shadow: 0 4px 6px rgba(0,0,0,0.1);
}

.product-title {
  margin-bottom: 1rem;
  font-size: 1.5rem;
  font-weight: 600;
  color: var(--text-dark);
}

.rate-container {
  margin-bottom: 1.5rem;
  text-align: center;
}

.rate {
  font-size: 2.25rem;
  font-weight: 700;
  color: var(--primary-color);
}

.rate-description {
  font-size: 0.875rem;
  color: var(--text-light);
}

.period {
  margin-bottom: 1.5rem;
  text-align: center;
  color: var(--text-light);
}

.join-button {
  padding: 0.5rem 1.5rem;
  border: none;
  border-radius: 0.375rem;
  background-color: var(--primary-color);
  color: var(--white);
  cursor: pointer;
  transition: background-color 0.2s;
}

.join-button:hover {
  background-color: var(--primary-hover);
}
</style>