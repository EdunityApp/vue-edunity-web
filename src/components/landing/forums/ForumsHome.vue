<template>
  <HomeTemplate :isReactive="true">
    <div class="forums-home">
      <div class="forums-header">
        <h1 class="forums-title">Community Forums</h1>
        <p class="forums-subtitle">Connect, share, and learn with educators worldwide</p>
      </div>

      <div class="forums-container">
        <main class="forums-main">
          <section v-for="category in categories" :key="category.id" class="category-section">
            <div class="category-header">
              <div class="category-title">
                <span class="category-icon">{{ category.icon }}</span>
                <h2>{{ category.name }}</h2>
              </div>
            </div>

            <div class="subforums-list">
              <router-link
                v-for="forum in category.subForums"
                :key="forum.id"
                :to="`/forums/category/${forum.id}`"
                class="subforum-row"
              >
                <div class="subforum-info">
                  <div class="subforum-name">{{ forum.name }}</div>
                  <div class="subforum-desc">{{ forum.description }}</div>
                </div>

                <div class="subforum-stats">
                  <div class="stat-item">
                    <v-icon size="20" class="stat-icon">mdi-forum</v-icon>
                    <span>{{ forum.threadCount.toLocaleString() }}</span>
                  </div>
                  <div class="stat-item">
                    <v-icon size="20" class="stat-icon">mdi-message-text</v-icon>
                    <span>{{ forum.postCount.toLocaleString() }}</span>
                  </div>
                </div>

                <div class="subforum-latest">
                  <div v-if="forum.latestPost" class="latest-post">
                    <v-avatar size="32">
                      <v-img v-if="forum.latestPost.author.avatar" :src="forum.latestPost.author.avatar" />
                      <span v-else class="avatar-placeholder">{{ forum.latestPost.author.name.charAt(0).toUpperCase() }}</span>
                    </v-avatar>
                    <div class="latest-info">
                      <div class="latest-title">{{ forum.latestPost.title }}</div>
                      <div class="latest-meta">
                        by <strong>{{ forum.latestPost.author.name }}</strong> • {{ formatTime(forum.latestPost.timestamp) }}
                      </div>
                    </div>
                  </div>
                  <div v-else class="no-posts">No posts yet</div>
                </div>
              </router-link>
            </div>
          </section>
        </main>

        <aside class="forums-sidebar">
          <LabelledContainer title="Top contributors today">
            <p class="no-activity">No recent activity</p>
          </LabelledContainer>

          <LabelledContainer title="Currently online" class="currently-online">
            <div class="online-avatars">
              <v-avatar v-for="i in 8" :key="i" size="40" class="online-avatar">
                <v-img :src="`https://avatar.iran.liara.run/public/${i + 10}`" />
              </v-avatar>
              <div class="more-avatars">+{{ onlineUsers - 8 }}</div>
            </div>
          </LabelledContainer>

          <LabelledContainer title="Recent threads" class="recent-thread">
            <p class="no-activity">No recent thread</p>
          </LabelledContainer>

          <LabelledContainer title="Activities today" class="recent-thread">
            <p class="no-activity">No recent activity</p>
          </LabelledContainer>
        </aside>
      </div>
    </div>
  </HomeTemplate>
</template>

<script setup lang="ts">
import HomeTemplate from "@/templates/HomeTemplate.vue";
import LabelledContainer from "@/components/commons/LabelledContainer.vue";

interface LatestPost {
  title: string;
  author: {
    id: number;
    name: string;
    avatar: string;
  };
  timestamp: string;
  threadId: number;
}

interface SubForum {
  id: number;
  name: string;
  description: string;
  threadCount: number;
  postCount: number;
  latestPost?: LatestPost;
}

interface MainCategory {
  id: number;
  name: string;
  icon: string;
  subForums: SubForum[];
}

const categories: MainCategory[] = [
  {
    id: 1,
    name: "Announcements",
    icon: "📢",
    subForums: [
      {
        id: 1,
        name: "General Announcements",
        description: "Important updates from the Quizlash team",
        threadCount: 8,
        postCount: 24,
        latestPost: {
          title: "Quizlash Beta is now live!",
          author: {
            id: 1,
            name: "Alex Carter",
            avatar: "https://avatar.iran.liara.run/public/1",
          },
          timestamp: "2025-11-18T14:30:00Z",
          threadId: 101,
        },
      },
      {
        id: 2,
        name: "Changelogs",
        description: "Detailed release notes and version history",
        threadCount: 15,
        postCount: 89,
        latestPost: {
          title: "v1.4.2 - AI question improvements & bug fixes",
          author: {
            id: 2,
            name: "Maya Singh",
            avatar: "https://avatar.iran.liara.run/public/22",
          },
          timestamp: "2025-11-17T10:15:00Z",
          threadId: 102,
        },
      },
      {
        id: 3,
        name: "Event Announcements",
        description: "Tournaments, webinars, and community events",
        threadCount: 4,
        postCount: 67,
        latestPost: {
          title: "December Global Quiz Battle - $500 Prize Pool",
          author: {
            id: 1,
            name: "Alex Carter",
            avatar: "https://avatar.iran.liara.run/public/1",
          },
          timestamp: "2025-11-16T09:00:00Z",
          threadId: 103,
        },
      },
    ],
  },
  {
    id: 2,
    name: "General",
    icon: "💬",
    subForums: [
      {
        id: 4,
        name: "Lounge",
        description: "Off-topic discussions and casual chat",
        threadCount: 156,
        postCount: 2893,
        latestPost: {
          title: "What are you quizzing today?",
          author: {
            id: 5,
            name: "Sarah Kim",
            avatar: "https://avatar.iran.liara.run/public/78",
          },
          timestamp: "2025-11-18T16:45:00Z",
          threadId: 201,
        },
      },
      {
        id: 5,
        name: "Showcase",
        description: "Share your best quiz battles and creations",
        threadCount: 67,
        postCount: 512,
        latestPost: {
          title: "My students broke the leaderboard with 98% accuracy!",
          author: {
            id: 3,
            name: "Leo Nakamura",
            avatar: "https://avatar.iran.liara.run/public/45",
          },
          timestamp: "2025-11-18T12:20:00Z",
          threadId: 202,
        },
      },
      {
        id: 6,
        name: "Tips & Tricks",
        description: "Share teaching strategies and Quizlash hacks",
        threadCount: 89,
        postCount: 734,
      },
    ],
  },
  {
    id: 3,
    name: "Help & Support",
    icon: "❓",
    subForums: [
      {
        id: 7,
        name: "Questions",
        description: "Ask the community for help",
        threadCount: 123,
        postCount: 892,
        latestPost: {
          title: "How do I export battle results to Google Sheets?",
          author: {
            id: 8,
            name: "Emma Wilson",
            avatar: "https://avatar.iran.liara.run/public/67",
          },
          timestamp: "2025-11-18T15:10:00Z",
          threadId: 301,
        },
      },
      {
        id: 8,
        name: "Bug Reports",
        description: "Report issues you're experiencing",
        threadCount: 45,
        postCount: 278,
      },
      {
        id: 9,
        name: "Feature Requests",
        description: "Suggest new ideas for Quizlash",
        threadCount: 98,
        postCount: 645,
        latestPost: {
          title: "Request: Custom timer per question",
          author: {
            id: 10,
            name: "David Chen",
            avatar: "https://avatar.iran.liara.run/public/89",
          },
          timestamp: "2025-11-18T11:30:00Z",
          threadId: 302,
        },
      },
    ],
  },
  {
    id: 4,
    name: "Community",
    icon: "❤️",
    subForums: [
      {
        id: 10,
        name: "Introductions",
        description: "New here? Say hello!",
        threadCount: 134,
        postCount: 567,
        latestPost: {
          title: "Hey everyone! History teacher from Canada here",
          author: {
            id: 11,
            name: "Rachel Green",
            avatar: "https://avatar.iran.liara.run/public/34",
          },
          timestamp: "2025-11-18T17:05:00Z",
          threadId: 401,
        },
      },
      {
        id: 11,
        name: "Feedback",
        description: "Tell us what you think about Quizlash",
        threadCount: 78,
        postCount: 456,
      },
    ],
  },
];

const onlineUsers = 48;

const formatTime = (iso: string): string => {
  const date = new Date(iso);
  const now = new Date();
  const diffMs = now.getTime() - date.getTime();
  const diffMins = Math.floor(diffMs / 60000);
  const diffHours = Math.floor(diffMs / 3600000);
  const diffDays = Math.floor(diffMs / 86400000);

  if (diffMins < 1) return "just now";
  if (diffMins < 60) return `${diffMins}m ago`;
  if (diffHours < 24) return `${diffHours}h ago`;
  if (diffDays < 7) return `${diffDays}d ago`;
  return date.toLocaleDateString();
};
</script>

<style scoped lang="scss">
@use "@styles/common.scss" as *;

.forums-home {
  min-height: 100vh;
  background: linear-gradient(to bottom, #ffffff, #eef7ff);

  .forums-header {
    text-align: center;
    padding: 8rem 2rem 3rem;

    .forums-title {
      font-size: 50px;
      font-weight: 600;
      background: linear-gradient(to right, $primary-color, $quaternary-color);
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
      display: inline-block;
      margin: 0 0 0.5rem;
    }

    .forums-subtitle {
      font-size: 1.25rem;
      color: #64748b;
      margin-bottom: 2rem;
    }
  }

  .forums-container {
    max-width: 1400px;
    margin: 0 auto;
    padding: 0 2rem 6rem;
    display: grid;
    grid-template-columns: 1fr 280px;
    gap: 3rem;
  }

  .forums-main {
    display: flex;
    flex-direction: column;
    gap: 2.5rem;
  }

  .category-section {
    background: #fff;
    border-radius: 0.6rem;
    overflow: hidden;
    box-shadow: 0 8px 32px rgba(0, 0, 0, 0.07);
    transition: all 0.3s;

    &:hover {
      box-shadow: 0 12px 40px rgba(0, 0, 0, 0.1);
    }

    .category-header {
      background: linear-gradient(to right, $primary-color, $quaternary-color);
      padding: 0.5rem 2rem;
      color: white;

      .category-title {
        display: flex;
        align-items: center;
        gap: 1rem;

        .category-icon {
          font-size: 1.5rem;
        }

        h2 {
          font-size: 1.5rem;
          font-weight: 600;
          margin: 0;
        }
      }
    }

    .subforums-list {
      .subforum-row {
        display: grid;
        grid-template-columns: 1.8fr 0.6fr 1.2fr;
        padding: 1.4rem 2rem;
        border-bottom: 1px solid #f1f5f9;
        transition: background 0.2s;
        text-decoration: none;
        color: inherit;

        &:hover {
          background: #f8fafc;
        }

        &:last-child {
          border-bottom: none;
        }

        .subforum-info {
          .subforum-name {
            font-size: 1.15rem;
            font-weight: 600;
            margin-bottom: 0.35rem;
            color: #1e293b;
          }

          .subforum-desc {
            font-size: 0.95rem;
            color: #64748b;
          }
        }

        .subforum-stats {
          display: flex;
          gap: 2rem;
          align-items: center;
          justify-content: center;

          .stat-item {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 0.35rem;
            font-size: 0.9rem;
            color: #475569;

            .stat-icon {
              color: #94a3b8;
            }
          }
        }

        .subforum-latest {
          display: flex;
          align-items: center;
          gap: 1rem;
          font-size: 0.93rem;

          .latest-post {
            display: flex;
            align-items: center;
            gap: 0.75rem;
            flex: 1;

            .latest-info {
              .latest-title {
                font-weight: 600;
                color: #1e293b;
                margin-bottom: 0.2rem;
                display: -webkit-box;
                -webkit-line-clamp: 1;
                -webkit-box-orient: vertical;
                overflow: hidden;
              }

              .latest-meta {
                color: #64748b;
                font-size: 0.85rem;
              }
            }
          }

          .no-posts {
            color: #94a6b8;
            font-style: italic;
          }
        }
      }
    }
  }

  .forums-sidebar {
    .online-avatars {
      display: flex;
      flex-wrap: wrap;
      gap: 0.75rem;

      .online-avatar {
        border: 3px solid #10b981;
        box-shadow: 0 0 0 2px #fff;
      }

      .more-avatars {
        width: 40px;
        height: 40px;
        background: #e2e8f0;
        border-radius: 50%;
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 0.85rem;
        font-weight: 600;
        color: #475569;
      }
    }

    .no-activity {
      color: #94a3b8;
      text-align: center;
      padding: 1rem;
      font-style: italic;
    }
  }

  .currently-online,
  .recent-thread {
    margin-top: 20px;
  }

  .avatar-placeholder {
    width: 100%;
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    background: linear-gradient(135deg, $primary-color, $quaternary-color);
    color: white;
    font-weight: 600;
    border-radius: 50%;
  }

  @media (max-width: 1100px) {
    .forums-container {
      grid-template-columns: 1fr;
    }

    .subforum-row {
      grid-template-columns: 1fr !important;
      gap: 1rem;

      .subforum-stats {
        order: 3;
        justify-content: flex-start !important;
      }

      .subforum-latest {
        padding-top: 0.5rem;
        border-top: 1px dashed #e2e8f0;
      }
    }
  }

  @media (max-width: 640px) {
    .subforum-stats {
      gap: 1.5rem !important;
    }
  }
}
</style>
