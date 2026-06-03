<!-- src/components/Contact.vue -->
<template>
  <section id="contact">
    <div class="container">
      <h2>Get In Touch</h2>
      <div class="contact-content glass-card">
        <p class="contact-text">
          I'm always open to interesting conversations, collaborations, or opportunities.
          Feel free to reach out!
        </p>
        
        <div class="contact-links">
          <a href="mailto:alex@example.com" class="contact-item">
            <span class="contact-icon">✉️</span>
            <span>joshuakittot@gmail.com</span>
          </a>
          <a href="https://github.com" target="_blank" class="contact-item">
            <span class="contact-icon">🐙</span>
            <span>github.com/joshuakittot</span>
          </a>
          <a href="https://linkedin.com" target="_blank" class="contact-item">
            <span class="contact-icon">🔗</span>
            <span>linkedin.com/in/joshuakittot</span>
          </a>
          <a href="https://twitter.com" target="_blank" class="contact-item">
            <span class="contact-icon">🐦</span>
            <span>@joshuakittot</span>
          </a>
        </div>
        
        <div class="availability">
          <span class="status-dot"></span>
          Open for freelance & full-time opportunities
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.contact-content {
  max-width: 600px;
  margin: 0 auto;
  padding: 2.5rem;
  text-align: center;
}

.contact-text {
  color: #d4d4d8;
  margin-bottom: 2rem;
}

.contact-links {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  margin-bottom: 2rem;
}

.contact-item {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.75rem;
  padding: 0.75rem;
  background: rgba(59, 130, 246, 0.1);
  border-radius: 12px;
  text-decoration: none;
  color: #e4e4e7;
  transition: all 0.3s ease;
}

.contact-item:hover {
  background: rgba(59, 130, 246, 0.2);
  transform: translateX(8px);
}

.contact-icon {
  font-size: 1.2rem;
}

.availability {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
  padding-top: 1rem;
  border-top: 1px solid rgba(59, 130, 246, 0.2);
  font-size: 0.9rem;
  color: #a1a1aa;
}

.status-dot {
  width: 8px;
  height: 8px;
  background: #10b981;
  border-radius: 50%;
  animation: pulse 2s infinite;
}

@keyframes pulse {
  0%, 100% {
    opacity: 1;
    transform: scale(1);
  }
  50% {
    opacity: 0.5;
    transform: scale(1.2);
  }
}
</style>