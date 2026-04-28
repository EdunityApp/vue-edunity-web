<template>
  <HomeTemplate :isReactive="true">
    <div class="mission-page">
      <div class="hero-section">
        <div class="hero-content">
          <h1 class="hero-title">Our Mission</h1>
          <p class="hero-subtitle">Empowering every learner to unlock their full potential</p>
          <div class="hero-statement">
            <v-icon size="32" color="#FFF">mdi-format-quote-open</v-icon>
            <p>Education does not change the world. Education changes people. People change the world.</p>
            <p class="quote-author">- Paulo Freire</p>
          </div>
        </div>
      </div>

      <div class="mission-grid">
        <div class="mission-card mission">
          <div class="card-header">
            <div class="card-icon">
              <v-icon size="56" color="#4A90E2">mdi-bullseye</v-icon>
            </div>
            <h2>What we strike for</h2>
          </div>

          <p>Our primary goal is to create engaging, adaptive learning experiences that meet every learner where they
            are and guide them toward where they aspire to go. We are committed to fostering a supportive and inclusive
            community where knowledge is shared, curiosity is encouraged, and every individual is empowered to grow with
            confidence and purpose.</p>
        </div>
      </div>

      <div class="impact-section">
        <h2 class="section-title">Our Impact Goals</h2>
        <div class="impact-cards">
          <div v-for="(goal, index) in impactGoals" :key="index" class="impact-card">
            <div class="impact-number">{{ goal.number }}</div>
            <h3>{{ goal.title }}</h3>
            <p>{{ goal.description }}</p>
          </div>
        </div>
      </div>

      <div class="focus-areas">
        <h2 class="section-title">What drives us</h2>
        <div class="focus-grid">
          <div v-for="(area, index) in focusAreas" :key="index" class="focus-card">
            <div class="focus-icon" :style="{ backgroundColor: area.bgColor }">
              <v-icon size="32" :color="area.iconColor">{{ area.icon }}</v-icon>
            </div>
            <div class="focus-content">
              <h3>{{ area.title }}</h3>
              <p>{{ area.description }}</p>
            </div>

          </div>
        </div>
      </div>

      <div class="commitment-section">
        <div class="commitment-content">
          <h2>Our Commitment</h2>
          <div class="commitment-list">
            <div v-for="(item, index) in commitments" :key="index" class="commitment-item">
              <v-icon color="#4A90E2" size="24">mdi-check-circle</v-icon>
              <span>{{ item }}</span>
            </div>
          </div>
        </div>
        <div class="commitment-visual">
          <div class="stats-ring">
            <div class="ring-stat">
              <div class="ring-number">100%</div>
              <div class="ring-label">Commitment to Quality</div>
            </div>
          </div>
        </div>
      </div>

      <div class="cta-section">
        <h2>Join Our Mission</h2>
        <p>Be part of the movement transforming education for millions of learners worldwide.</p>
        <div class="cta-buttons">
          <v-btn to="/register" size="large" class="btn-get-started">Get Started</v-btn>
          <v-btn to="/contact" size="large">Partner With Us</v-btn>
        </div>
      </div>
    </div>
  </HomeTemplate>
</template>

<script setup>
import HomeTemplate from '@/templates/HomeTemplate.vue';

const impactGoals = [
  {
    number: "50M+",
    title: "Learners Reached",
    description: "Empower over 50 million students with personalized learning tools by 2030"
  },
  {
    number: "100K+",
    title: "Schools Partnered",
    description: "Collaborate with educational institutions across every continent"
  },
  {
    number: "100%",
    title: "Accessibility",
    description: "Make our platform fully accessible to learners with diverse needs"
  },
  {
    number: "Zero",
    title: "Cost Barriers",
    description: "Provide free access to underserved communities worldwide"
  }
];

const focusAreas = [
  {
    icon: "mdi-brain",
    title: "Personalized Learning",
    description: "AI-driven paths that adapt to each student's pace, style, and goals",
    bgColor: "rgba(74, 144, 226, 0.1)",
    iconColor: "#4A90E2"
  },
  {
    icon: "mdi-account-group",
    title: "Teacher Empowerment",
    description: "Tools that reduce administrative burden and enhance classroom impact",
    bgColor: "rgba(80, 227, 194, 0.1)",
    iconColor: "#50E3C2"
  },
  {
    icon: "mdi-chart-line",
    title: "Data-Driven Insights",
    description: "Actionable analytics to track progress and identify improvement areas",
    bgColor: "rgba(245, 166, 35, 0.1)",
    iconColor: "#F5A623"
  },
  {
    icon: "mdi-earth",
    title: "Global Community",
    description: "Connecting learners and educators across cultural boundaries",
    bgColor: "rgba(144, 19, 254, 0.1)",
    iconColor: "#9013FE"
  }
];

const commitments = [
  "Zero data compromise - Privacy by design",
  "Evidence-based learning methodologies",
  "Continuous innovation through research",
  "Inclusive design for all learners",
  "Sustainable and ethical technology"
];
</script>

<style lang="scss" scoped>
@use "./MissionsPage.scss" as *;
</style>
