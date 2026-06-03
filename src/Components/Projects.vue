<!-- src/components/Projects.vue -->
<template>
  <section id="projects">
    <div class="container">
      <h2>Featured Projects</h2>
      <div class="projects-grid">
        <div v-for="project in projects" :key="project.title" class="project-card glass-card">
          <div class="project-icon">{{ project.icon }}</div>
          <h3>{{ project.title }}</h3>
          <p>{{ project.description }}</p>
          <div class="tech-stack">
            <span v-for="tech in project.tech" :key="tech">{{ tech }}</span>
          </div>
          <div class="project-links">
            <a :href="project.github" target="_blank" class="project-link">GitHub →</a>
            <a :href="project.demo" target="_blank" class="project-link">Live Demo →</a>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const projects = [
  {
    icon: "🚀",
    title: "AI Code Assistant",
    description: "VS Code extension that provides intelligent code suggestions and refactoring using OpenAI API.",
    tech: ["TypeScript", "OpenAI", "VSCode API"],
    github: "#",
    demo: "#"
  },
  {
    icon: "📊",
    title: "Analytics Dashboard",
    description: "Real-time dashboard with interactive charts, user behavior tracking, and custom reporting.",
    tech: ["Vue.js", "D3.js", "Node.js", "WebSocket"],
    github: "#",
    demo: "#"
  },
  {
    icon: "🔗",
    title: "DevConnect",
    description: "Social platform for developers to share projects, find mentors, and collaborate.",
    tech: ["React", "Express", "MongoDB", "Socket.io"],
    github: "#",
    demo: "#"
  }
]
</script>

<style scoped>
.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
  gap: 2rem;
}

.project-card {
  padding: 1.5rem;
  transition: all 0.3s ease;
}

.project-icon {
  font-size: 3rem;
  margin-bottom: 1rem;
}

.project-card h3 {
  font-size: 1.3rem;
  margin-bottom: 0.75rem;
  color: white;
}

.project-card p {
  color: #a1a1aa;
  margin-bottom: 1rem;
  line-height: 1.6;
}

.tech-stack {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  margin-bottom: 1.5rem;
}

.tech-stack span {
  padding: 0.25rem 0.75rem;
  background: rgba(59, 130, 246, 0.1);
  border-radius: 50px;
  font-size: 0.75rem;
  color: #60a5fa;
}

.project-links {
  display: flex;
  gap: 1rem;
}

.project-link {
  color: #3b82f6;
  text-decoration: none;
  font-size: 0.9rem;
  transition: all 0.3s ease;
}

.project-link:hover {
  color: #60a5fa;
  transform: translateX(4px);
}
</style>