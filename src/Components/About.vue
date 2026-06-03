<!-- src/components/About.vue -->
<template>
  <section id="about">
    <div class="container">
      <h2>About Me</h2>
      <div class="about-content glass-card">
        <div class="about-text">
          <p>
            I'm a <strong>Software Engineer</strong> with 6+ years of experience building 
            scalable web applications and distributed systems. My journey started with a 
            curiosity for how things work, and evolved into a passion for creating 
            technology that makes a difference.
          </p>
          <p>
            I specialize in <strong>Vue.js, React, Node.js, PHP, and Python</strong>, but I'm 
            always exploring new tools and paradigms. I believe in clean code, thoughtful 
            architecture, and continuous learning.
          </p>
          <p>
            When I'm not coding, you'll find me contributing to open source, mentoring 
            junior developers, or exploring the latest in AI and cloud computing.
          </p>
          
          <div class="highlights">
            <div class="highlight">
              <span class="emoji">🎓</span>
              <span> Computer Science</span>
            </div>
            <div class="highlight">
              <span class="emoji">🏆</span>
              <span>Hackathon Winner 2020</span>
            </div>
            <div class="highlight">
              <span class="emoji">📝</span>
              <span>Technical Writer</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.about-content {
  padding: 2.5rem;
  max-width: 800px;
  margin: 0 auto;
}

.about-text p {
  margin-bottom: 1.2rem;
  color: #d4d4d8;
  line-height: 1.8;
}

.about-text strong {
  color: #60a5fa;
}

.highlights {
  display: flex;
  gap: 2rem;
  justify-content: center;
  margin-top: 2rem;
  flex-wrap: wrap;
}

.highlight {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.5rem 1rem;
  background: rgba(59, 130, 246, 0.1);
  border-radius: 50px;
  font-size: 0.9rem;
}

.emoji {
  font-size: 1.2rem;
}
</style>