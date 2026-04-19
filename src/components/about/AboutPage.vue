<template>
  <HomeTemplate :isReactive="true">
    <div class="about-page">
      <div class="about-container">
        <div class="about-header">
          <h1 class="about-title">About Edunity</h1>
          <p class="about-subtitle">
            We're crafting the next generation of interactive, AI-driven
            learning experiences.
          </p>
        </div>

        <div class="about-story">
          <div class="story-text">
            <h2>Our story</h2>
            <p>
              Edunity began in late 2025 with a dream to make learning
              exciting, engaging, and community-powered. We believe that
              education shouldn't feel like a chore—it should spark curiosity
              and connection.
            </p>
            <p>
              From our humble beginnings to our first beta launch, our mission
              has remained the same: transform how people learn, teach, and
              test knowledge through creativity and collaboration.
            </p>
            <p>
              With an AI-driven core and a passionate community, we're
              building a world where quizzes inspire discovery and every
              learner finds joy in progress.
            </p>
          </div>

          <div class="story-image">
            <div class="story-img-placeholder">
              <v-icon size="80" color="#4A90E2">mdi-school</v-icon>
            </div>
          </div>
        </div>

        <div class="about-mission-vision">
          <v-row>
            <v-col cols="12" md="6">
              <div class="mission-card">
                <v-icon size="48" color="#4A90E2">mdi-target</v-icon>
                <h3>Our Mission</h3>
                <p>To democratize education by making engaging, personalized learning accessible to every student,
                  teacher, and institution worldwide.</p>
              </div>
            </v-col>
            <v-col cols="12" md="6">
              <div class="vision-card">
                <v-icon size="48" color="#50E3C2">mdi-eye</v-icon>
                <h3>Our Vision</h3>
                <p>A world where technology and human connection unite to create transformative learning experiences
                  that inspire lifelong curiosity.</p>
              </div>
            </v-col>
          </v-row>
        </div>

        <div class="about-values">
          <h2 class="values-title">Our core values</h2>
          <v-row>
            <v-col v-for="(value, index) in coreValues" :key="index" cols="12" sm="6" md="3">
              <div class="value-card">
                <v-icon size="40" :color="value.color">{{ value.icon }}</v-icon>
                <h4>{{ value.title }}</h4>
                <p>{{ value.description }}</p>
              </div>
            </v-col>
          </v-row>
        </div>

        <div class="about-journey">
          <h2 class="journey-title">The milestone we once dreamed of</h2>

          <v-timeline align="alternate" line-color="secondary">
            <v-timeline-item v-for="(milestone, index) in milestones" :key="index" class="timeline-item"
              dot-color="secondary" size="small">
              <template #icon>
                <v-icon :color="milestone.color">{{ milestone.icon }}</v-icon>
              </template>
              <div class="timeline-content">
                <h3>{{ milestone.month }}</h3>
                <hr />

                <h4>{{ milestone.title }}</h4>
                <p>{{ milestone.description }}</p>
              </div>
            </v-timeline-item>
          </v-timeline>
        </div>

        <div class="about-stats">
          <h2 class="stats-title">Up until this point, our team has provided for</h2>

          <v-row class="stats-grid">
            <v-col v-for="(stat, index) in companyStats" :key="index" cols="6" md="3">
              <div class="stat-card">
                <div class="stat-number">{{ stat.value }}</div>
                <div class="stat-label">{{ stat.label }}</div>
              </div>
            </v-col>
          </v-row>
        </div>

        <div class="about-future">
          <h2 class="future-title">But it's only the start</h2>
          <p>
            It's not over for us. This journey has just begun. We are committed to redefining further how education
            works
            around the world, alongside the best way to make learning more interesting and engaging for students around the world, one step at a time!
          </p>
          <p>So what are we waiting for?</p>
          <div class="future-cta">
            <v-btn to="/register" color="#4A90E2" size="large" class="future-btn">
              Join our journey
            </v-btn>
            <v-btn variant="outlined" color="#4A90E2" size="large">
              Contact us
            </v-btn>
          </div>
        </div>
      </div>
    </div>
  </HomeTemplate>
</template>

<script setup>
import HomeTemplate from "../../templates/HomeTemplate";

const coreValues = [
  {
    icon: "mdi-lightbulb-on",
    title: "Innovation",
    description: "Constantly pushing boundaries to create cutting-edge learning solutions",
    color: "#FF6B6B"
  },
  {
    icon: "mdi-account-group",
    title: "Community",
    description: "Building a global network of educators and learners who support each other",
    color: "#4ECDC4"
  },
  {
    icon: "mdi-access-point",
    title: "Accessibility",
    description: "Making quality education available to everyone, everywhere",
    color: "#45B7D1"
  },
  {
    icon: "mdi-chart-line",
    title: "Excellence",
    description: "Delivering the highest quality learning experiences and outcomes",
    color: "#96CEB4"
  }
];

const milestones = [
  {
    month: "September 2025",
    title: "The beginning",
    description: "Edunity was founded with a vision to revolutionize learning through gamification and AI-driven personalization.",
    icon: "mdi-rocket-launch",
    color: "#4A90E2"
  },
  {
    month: "October 2025",
    title: "First beta launch",
    description: "Released our beta version, empowering early adopters to create and play interactive quizzes with real-time feedback.",
    icon: "mdi-trophy",
    color: "#50E3C2"
  },
  {
    month: "December 2025",
    title: "10,000 Users",
    description: "Reached our first major milestone with 10,000 active educators and students joining our platform.",
    icon: "mdi-chart-line",
    color: "#F5A623"
  },
  {
    month: "February 2026",
    title: "Global Recognition",
    description: "Awarded 'Best EdTech Innovation' at the Southeast Asia Education Summit.",
    icon: "mdi-medal",
    color: "#D0021B"
  },
  {
    month: "April 2026",
    title: "AI Learning Engine",
    description: "Launched our proprietary AI engine that personalizes learning paths for every student.",
    icon: "mdi-robot",
    color: "#9013FE"
  }
];

const companyStats = [
  { value: "50K+", label: "Active Users" },
  { value: "120+", label: "Countries" },
  { value: "500+", label: "Institutions" },
];
</script>

<style lang="scss" scoped>
@use "@styles/common.scss" as *;

.about-page {
  min-height: 100vh;
  background: linear-gradient(135deg, #fff 0%, #d2f1ff 50%, #fdd4ff 100%);

  .about-container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 8rem 2rem;
  }

  .about-header {
    text-align: center;
    margin-bottom: 5rem;

    .about-title {
      font-size: 64px;
      font-weight: 700;
      background: linear-gradient(135deg, $primary-color, $secondary-color);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      margin-bottom: 1.5rem;
      animation: fadeInUp 0.8s ease;
    }

    .about-subtitle {
      font-size: 1.5rem;
      color: #64748b;
      max-width: 700px;
      margin: 0 auto;
      animation: fadeInUp 0.8s ease 0.2s both;
    }
  }

  .about-story {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 4rem;
    align-items: center;
    margin-bottom: 5rem;

    .story-text {
      h2 {
        font-size: 2.5rem;
        font-weight: 700;
        background: linear-gradient(135deg, $primary-color, $secondary-color);
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
        margin-bottom: 1.5rem;
      }

      p {
        color: #475569;
        line-height: 1.8;
        margin-bottom: 1.25rem;
        font-size: 1.05rem;
      }
    }

    .story-image {
      .story-img-placeholder {
        background: linear-gradient(135deg, rgba(74, 144, 226, 0.1), rgba(80, 227, 194, 0.1));
        border-radius: 1.5rem;
        height: 350px;
        display: flex;
        align-items: center;
        justify-content: center;
        box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
        transition: transform 0.3s ease;

        &:hover {
          transform: scale(1.02);
        }
      }
    }
  }

  .about-mission-vision {
    margin-bottom: 5rem;

    .mission-card,
    .vision-card {
      background: white;
      border-radius: 1.5rem;
      padding: 2rem;
      text-align: center;
      box-shadow: 0 10px 30px rgba(0, 0, 0, 0.05);
      transition: all 0.3s ease;
      height: 100%;

      &:hover {
        transform: translateY(-5px);
        box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
      }

      h3 {
        font-size: 1.5rem;
        font-weight: 600;
        margin: 1rem 0;
        color: #1a202c;
      }

      p {
        color: #64748b;
        line-height: 1.6;
      }
    }
  }

  .about-values {
    margin-bottom: 5rem;
    text-align: center;

    .values-title {
      font-size: 2.5rem;
      font-weight: 700;
      background: linear-gradient(135deg, $primary-color, $secondary-color);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      margin-bottom: 3rem;
    }

    .value-card {
      background: white;
      border-radius: 1rem;
      padding: 1.5rem;
      text-align: center;
      transition: all 0.3s ease;
      height: 100%;

      &:hover {
        transform: translateY(-5px);
        box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
      }

      h4 {
        font-size: 1.2rem;
        font-weight: 600;
        margin: 1rem 0 0.5rem;
        color: #1a202c;
      }

      p {
        color: #64748b;
        font-size: 0.9rem;
        line-height: 1.5;
      }
    }
  }

  .about-journey {
    margin-bottom: 5rem;
    text-align: center;

    .journey-title {
      font-size: 2.5rem;
      font-weight: 700;
      background: linear-gradient(135deg, $primary-color, $secondary-color);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      margin-bottom: 3rem;
    }

    .timeline-content {
      text-align: left;

      h3 {
        font-size: 1.2rem;
        font-weight: 600;
        color: $primary-color;
        margin-bottom: 0.25rem;
      }

      h4 {
        font-size: 1.1rem;
        font-weight: 500;
        margin-bottom: 0.5rem;
      }

      p {
        color: #64748b;
        line-height: 1.5;
      }
    }

    .timeline-content {
      // transform: translateY(-18px) !important;
    }
  }

  .about-team {
    margin-bottom: 5rem;
    text-align: center;

    .team-title {
      font-size: 2.5rem;
      font-weight: 700;
      background: linear-gradient(135deg, $primary-color, $secondary-color);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      margin-bottom: 3rem;
    }

    .team-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 2rem;
    }

    .team-card {
      text-align: center;
      transition: all 0.3s ease;
      border-radius: 1rem;

      &:hover {
        transform: translateY(-8px);
        box-shadow: 0 20px 40px rgba(0, 0, 0, 0.15);
      }

      .team-image-container {
        margin-bottom: 1rem;

        .team-image-placeholder {
          width: 120px;
          height: 120px;
          margin: 0 auto;
          background: linear-gradient(135deg, rgba(74, 144, 226, 0.1), rgba(80, 227, 194, 0.1));
          border-radius: 50%;
          display: flex;
          align-items: center;
          justify-content: center;
        }
      }

      h3 {
        font-size: 1.3rem;
        font-weight: 600;
        margin-bottom: 0.25rem;
        color: #1a202c;
      }

      .team-role {
        color: $primary-color;
        font-weight: 500;
        margin-bottom: 0.75rem;
      }

      .team-bio {
        color: #64748b;
        font-size: 0.9rem;
        line-height: 1.5;
        margin-bottom: 1rem;
      }

      .team-social {
        display: flex;
        justify-content: center;
        gap: 1rem;
        padding-top: 0.5rem;
        border-top: 1px solid #e2e8f0;

        .social-icon {
          cursor: pointer;
          color: #94a3b8;
          transition: color 0.3s ease;

          &:hover {
            color: $primary-color;
          }
        }
      }
    }
  }

  .about-stats {
    margin-bottom: 5rem;
    padding: 3rem;
    background: rgba(255, 255, 255, 0.6);
    border-radius: 2rem;
    backdrop-filter: blur(10px);

    .stats-title {
      text-align: center;
      margin-bottom: 25px;
      font-size: 34px;
      background: linear-gradient(to bottom, $primary-color, $tertiary-color);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
    }

    .stats-grid {
      justify-content: center !important;
    }

    .stat-card {
      text-align: center;

      .stat-number {
        font-size: 2.5rem;
        font-weight: 700;
        background: linear-gradient(135deg, $primary-color, $secondary-color);
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
        margin-bottom: 0.5rem;
      }

      .stat-label {
        color: #64748b;
        font-size: 1rem;
      }
    }
  }

  .about-future {
    text-align: center;
    max-width: 800px;
    margin: 0 auto;

    .future-title {
      font-size: 2.5rem;
      font-weight: 700;
      background: linear-gradient(135deg, $primary-color, $secondary-color);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      margin-bottom: 1.5rem;
    }

    p {
      font-size: 1.125rem;
      color: #475569;
      line-height: 1.8;
      margin-bottom: 2rem;
    }

    .future-cta {
      display: flex;
      gap: 1rem;
      justify-content: center;
      flex-wrap: wrap;

      .future-btn {
        background: linear-gradient(135deg, $primary-color, $secondary-color);
        color: white;
        text-transform: none;
        font-weight: 600;
      }
    }
  }
}

@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(30px);
  }

  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@media (max-width: 768px) {
  .about-page {
    .about-container {
      padding: 6rem 1.5rem;
    }

    .about-header {
      .about-title {
        font-size: 48px;
      }

      .about-subtitle {
        font-size: 1.2rem;
      }
    }

    .about-story {
      grid-template-columns: 1fr;
      gap: 2rem;
    }

    .about-journey {
      .timeline-content {
        text-align: center;
      }
    }

    .about-stats {
      padding: 2rem;
    }
  }
}
</style>
