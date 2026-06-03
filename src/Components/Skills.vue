<!-- src/components/Skills.vue -->
<template>
  <section id="skills">
    <div class="container">
      <h2>Tech Stack</h2>
      <div class="skills-grid">
        <div v-for="category in skills" :key="category.name" class="skill-category glass-card">
          <h3>{{ category.name }}</h3>
          <div class="skill-items">
            <span v-for="skill in category.items" :key="skill" class="skill-tag">
              {{ skill }}
            </span>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const skills = [
  {
    name: "Frontend",
    items: ["Vue.js", "React", "TypeScript", "Tailwind CSS", "Next.js"]
  },
  {
    name: "Backend",
    items: ["Node.js", "PHP", "Python", "Go", "PostgreSQL", "MongoDB"]
  },
  {
    name: "DevOps & Tools",
    items: ["Docker", "Kubernetes", "AWS", "Git", "CI/CD"]
  }
]
</script>

<style scoped>
.skills-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 1.5rem;
}

.skill-category {
  padding: 1.5rem;
}

.skill-category h3 {
  font-size: 1.3rem;
  margin-bottom: 1rem;
  color: #60a5fa;
}

.skill-items {
  display: flex;
  flex-wrap: wrap;
  gap: 0.75rem;
}

.skill-tag {
  padding: 0.4rem 1rem;
  background: rgba(59, 130, 246, 0.15);
  border: 1px solid rgba(59, 130, 246, 0.3);
  border-radius: 50px;
  font-size: 0.85rem;
  transition: all 0.3s ease;
}

.skill-tag:hover {
  background: rgba(59, 130, 246, 0.3);
  transform: scale(1.05);
}
</style>