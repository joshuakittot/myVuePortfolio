<!-- src/components/Hero.vue (Updated with Resume Modal) -->
<template>
  <section class="hero">
    <div class="container">
      <div class="hero-content glass-card">
        <div class="badge">✦ Software Engineer</div>
        <h1>Joshua Kittot</h1>
        <div class="typed-wrapper">
          <span class="prefix">I </span>
          <span ref="typedElement" class="typed-text"></span>
        </div>
        <p class="tagline">
          Building elegant solutions with clean code, modern architecture, 
          and a passion for exceptional user experiences.
        </p>
        <div class="cta-buttons">
          <a href="#projects" class="btn btn-primary">View Work</a>
          <a href="#contact" class="btn btn-secondary">Contact Me</a>
          <button @click="openResumeModal" class="btn btn-outline">Resume</button>
        </div>
        
        <div class="code-snippet">
          <pre><code>&gt; const engineer = {<br>  name: "Joshua Kittot",<br>  role: "Software Engineer",<br>  passion: "Building great things"<br>};<br>&gt; engineer.build();</code></pre>
        </div>
      </div>
    </div>

    <!-- Resume Modal -->
    <div v-if="showModal" class="modal-overlay" @click="closeModalOnOverlay">
      <div class="modal-container glass-card">
        <div class="modal-header">
          <h2>📄 Resume</h2>
          <button class="modal-close" @click="closeModal">×</button>
        </div>
        
        <div class="modal-body">
          <!-- Resume Content -->
          <div class="resume-section">
            <h3>Joshua Kittot</h3>
            <p class="resume-title">Senior Software Engineer</p>
            <div class="resume-contact">
              <span>📧 joshuakittot@gmail.com</span>
              <span>📱 +254 713 763 145</span>
              <span>📍 Westlands, Nairobi</span>
            </div>
          </div>

          <div class="resume-section">
            <h4>💼 Professional Experience</h4>
            
            <div class="experience-item">
              <div class="exp-header">
                <strong>Senior Software Engineer</strong>
                <span class="exp-date">2022 – Present</span>
              </div>
              <div class="exp-company">TechCorp Innovations</div>
              <ul>
                <li>Led development of microservices architecture serving 1M+ users</li>
                <li>Improved API response time by 40% through optimization and caching</li>
                <li>Mentored 5 junior developers and conducted code reviews</li>
              </ul>
            </div>

            <div class="experience-item">
              <div class="exp-header">
                <strong>Full Stack Developer</strong>
                <span class="exp-date">2019 – 2022</span>
              </div>
              <div class="exp-company">Digital Solutions Inc.</div>
              <ul>
                <li>Built responsive web applications using Vue.js and Node.js</li>
                <li>Implemented CI/CD pipeline reducing deployment time by 60%</li>
                <li>Collaborated with design team to improve UX metrics by 25%</li>
              </ul>
            </div>
          </div>

          <div class="resume-section">
            <h4>🎓 Education</h4>
            <div class="experience-item">
              <div class="exp-header">
                <strong>Computer Science</strong>
                <span class="exp-date">2017 – 2019</span>
              </div>
              <div>Pwani University | GPA: 3.9/4.0</div>
            </div>
            <div class="experience-item">
              <div class="exp-header">
                <strong>B.S. in Software Engineering</strong>
                <span class="exp-date">2013 – 2017</span>
              </div>
              <div>Pwani University</div>
            </div>
          </div>

          <div class="resume-section">
            <h4>🛠️ Technical Skills</h4>
            <div class="skills-resume">
              <span class="skill-badge">JavaScript/TypeScript</span>
              <span class="skill-badge">Vue.js</span>
              <span class="skill-badge">React</span>
              <span class="skill-badge">Node.js</span>
              <span class="skill-badge">Python</span>
              <span class="skill-badge">Docker</span>
              <span class="skill-badge">AWS</span>
              <span class="skill-badge">PostgreSQL</span>
              <span class="skill-badge">MongoDB</span>
              <span class="skill-badge">Git</span>
            </div>
          </div>

          <div class="resume-section">
            <h4>🏆 Achievements</h4>
            <ul>
              <li>Hackathon Winner 2023 - Best AI Application</li>
              <li>Published Technical Articles on Medium (50K+ reads)</li>
            </ul>
          </div>
        </div>

        <div class="modal-footer">
          <button @click="downloadResume" class="btn btn-primary">
            📥 Download PDF
          </button>
          <button @click="closeModal" class="btn btn-secondary">
            Close
          </button>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { onMounted, ref } from 'vue'

const typedElement = ref(null)
const showModal = ref(false)

// Typing animation
onMounted(() => {
  const words = ['build things.', 'solve problems.', 'create value.', 'write code.']
  let wordIndex = 0
  let charIndex = 0
  let isDeleting = false
  
  const type = () => {
    if (!typedElement.value) return
    
    const currentWord = words[wordIndex]
    
    if (isDeleting) {
      typedElement.value.textContent = currentWord.substring(0, charIndex - 1)
      charIndex--
    } else {
      typedElement.value.textContent = currentWord.substring(0, charIndex + 1)
      charIndex++
    }
    
    if (!isDeleting && charIndex === currentWord.length) {
      isDeleting = true
      setTimeout(type, 2000)
      return
    }
    
    if (isDeleting && charIndex === 0) {
      isDeleting = false
      wordIndex = (wordIndex + 1) % words.length
    }
    
    const speed = isDeleting ? 50 : 100
    setTimeout(type, speed)
  }
  
  type()
})

// Resume Modal Functions
const openResumeModal = () => {
  showModal.value = true
  document.body.style.overflow = 'hidden' // Prevent scrolling when modal is open
}

const closeModal = () => {
  showModal.value = false
  document.body.style.overflow = '' // Restore scrolling
}

const closeModalOnOverlay = (event) => {
  if (event.target.classList.contains('modal-overlay')) {
    closeModal()
  }
}

const downloadResume = () => {
  // Create a simple PDF download (in real scenario, you'd link to an actual PDF file)
  // For demo, we'll create a downloadable HTML version
  const resumeContent = document.querySelector('.modal-body').cloneNode(true)
  const styles = document.querySelector('style').innerHTML
  
  const win = window.open('', '_blank')
  win.document.write(`
    <!DOCTYPE html>
    <html>
    <head>
      <title>Joshua Kittot - Resume</title>
      <style>
        body {
          font-family: 'Inter', Arial, sans-serif;
          padding: 40px;
          max-width: 800px;
          margin: 0 auto;
          color: #333;
        }
        .resume-section {
          margin-bottom: 30px;
        }
        h3 {
          color: #2563eb;
          margin-bottom: 5px;
        }
        .resume-title {
          color: #666;
          margin-bottom: 15px;
        }
        .resume-contact {
          display: flex;
          gap: 20px;
          margin-bottom: 20px;
          color: #666;
        }
        h4 {
          color: #1e40af;
          border-bottom: 2px solid #3b82f6;
          padding-bottom: 5px;
        }
        .experience-item {
          margin-bottom: 20px;
        }
        .exp-header {
          display: flex;
          justify-content: space-between;
          font-weight: bold;
        }
        .exp-company {
          color: #666;
          margin: 5px 0 10px 0;
        }
        ul {
          margin-top: 5px;
          padding-left: 20px;
        }
        .skills-resume {
          display: flex;
          flex-wrap: wrap;
          gap: 8px;
        }
        .skill-badge {
          background: #e0e7ff;
          padding: 4px 12px;
          border-radius: 20px;
          font-size: 14px;
        }
        @media print {
          body {
            padding: 20px;
          }
        }
      </style>
    </head>
    <body>
      ${resumeContent.outerHTML}
      <p style="text-align: center; margin-top: 40px; color: #999;">
        Generated from Alex Rivera's Portfolio
      </p>
    </body>
    </html>
  `)
  win.document.close()
  win.print()
  
  // Alternative: In production, you'd link to an actual PDF file
  // window.open('/path-to-resume.pdf', '_blank')
}
</script>

<style scoped>
.hero {
  min-height: 100vh;
  display: flex;
  align-items: center;
  padding: 120px 0 80px;
}

.hero-content {
  padding: 3rem;
  text-align: center;
}

.badge {
  display: inline-block;
  padding: 0.5rem 1rem;
  background: rgba(59, 130, 246, 0.15);
  border: 1px solid rgba(59, 130, 246, 0.3);
  border-radius: 50px;
  font-size: 0.85rem;
  color: #60a5fa;
  margin-bottom: 1.5rem;
}

h1 {
  font-size: 4rem;
  background: linear-gradient(135deg, #fff, #3b82f6);
  -webkit-background-clip: text;
  background-clip: text;
  color: transparent;
  margin-bottom: 1rem;
}

.typed-wrapper {
  font-size: 1.8rem;
  margin-bottom: 1.5rem;
}

.prefix {
  color: #a1a1aa;
}

.typed-text {
  color: #3b82f6;
  border-right: 2px solid #3b82f6;
  padding-right: 5px;
}

.tagline {
  max-width: 600px;
  margin: 0 auto 2rem;
  color: #d4d4d8;
  font-size: 1.1rem;
}

.cta-buttons {
  display: flex;
  gap: 1rem;
  justify-content: center;
  flex-wrap: wrap;
  margin-bottom: 2.5rem;
}

.btn {
  padding: 0.75rem 1.5rem;
  border-radius: 12px;
  text-decoration: none;
  font-weight: 500;
  transition: all 0.3s ease;
  cursor: pointer;
  border: none;
  font-size: 1rem;
}

.btn-primary {
  background: #3b82f6;
  color: white;
}

.btn-primary:hover {
  background: #2563eb;
  transform: translateY(-2px);
  box-shadow: 0 10px 20px rgba(59, 130, 246, 0.3);
}

.btn-secondary {
  background: rgba(255, 255, 255, 0.1);
  color: white;
  border: 1px solid rgba(255, 255, 255, 0.2);
}

.btn-secondary:hover {
  background: rgba(255, 255, 255, 0.2);
  transform: translateY(-2px);
}

.btn-outline {
  background: transparent;
  border: 1px solid #3b82f6;
  color: #3b82f6;
}

.btn-outline:hover {
  background: rgba(59, 130, 246, 0.1);
  transform: translateY(-2px);
}

.code-snippet {
  background: rgba(0, 0, 0, 0.4);
  border-radius: 12px;
  padding: 1rem;
  text-align: left;
  max-width: 400px;
  margin: 0 auto;
  overflow-x: auto;
}

.code-snippet pre {
  font-family: 'Fira Code', monospace;
  font-size: 0.8rem;
  color: #10b981;
}

/* Modal Styles */
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.8);
  backdrop-filter: blur(8px);
  z-index: 1000;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 1rem;
  animation: fadeIn 0.3s ease;
}

.modal-container {
  max-width: 800px;
  width: 100%;
  max-height: 90vh;
  background: rgba(20, 20, 30, 0.95);
  backdrop-filter: blur(20px);
  border-radius: 24px;
  border: 1px solid rgba(59, 130, 246, 0.3);
  display: flex;
  flex-direction: column;
  animation: slideUp 0.3s ease;
}

.modal-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1.5rem 2rem;
  border-bottom: 1px solid rgba(59, 130, 246, 0.2);
}

.modal-header h2 {
  margin: 0;
  font-size: 1.5rem;
}

.modal-close {
  background: none;
  border: none;
  color: #a1a1aa;
  font-size: 2rem;
  cursor: pointer;
  transition: all 0.3s ease;
  line-height: 1;
}

.modal-close:hover {
  color: #ef4444;
  transform: scale(1.1);
}

.modal-body {
  padding: 2rem;
  overflow-y: auto;
  flex: 1;
}

.modal-body::-webkit-scrollbar {
  width: 6px;
}

.modal-body::-webkit-scrollbar-track {
  background: rgba(255, 255, 255, 0.05);
}

.modal-body::-webkit-scrollbar-thumb {
  background: #3b82f6;
  border-radius: 3px;
}

.resume-section {
  margin-bottom: 2rem;
}

.resume-section h3 {
  font-size: 1.8rem;
  color: white;
  margin-bottom: 0.25rem;
}

.resume-section h4 {
  font-size: 1.2rem;
  color: #60a5fa;
  margin-bottom: 1rem;
  border-left: 3px solid #3b82f6;
  padding-left: 0.75rem;
}

.resume-title {
  color: #a1a1aa;
  margin-bottom: 1rem;
}

.resume-contact {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
  padding: 1rem 0;
  border-bottom: 1px solid rgba(59, 130, 246, 0.2);
  margin-bottom: 1rem;
  color: #a1a1aa;
  font-size: 0.9rem;
}

.experience-item {
  margin-bottom: 1.5rem;
}

.exp-header {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  margin-bottom: 0.25rem;
}

.exp-header strong {
  color: white;
}

.exp-date {
  color: #a1a1aa;
  font-size: 0.85rem;
}

.exp-company {
  color: #60a5fa;
  margin-bottom: 0.5rem;
  font-size: 0.9rem;
}

.experience-item ul {
  margin-left: 1.25rem;
  color: #d4d4d8;
}

.experience-item li {
  margin-bottom: 0.25rem;
}

.skills-resume {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
}

.skill-badge {
  padding: 0.25rem 0.75rem;
  background: rgba(59, 130, 246, 0.15);
  border: 1px solid rgba(59, 130, 246, 0.3);
  border-radius: 50px;
  font-size: 0.85rem;
  color: #60a5fa;
}

.modal-footer {
  padding: 1.5rem 2rem;
  border-top: 1px solid rgba(59, 130, 246, 0.2);
  display: flex;
  gap: 1rem;
  justify-content: flex-end;
}

@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

@keyframes slideUp {
  from {
    transform: translateY(50px);
    opacity: 0;
  }
  to {
    transform: translateY(0);
    opacity: 1;
  }
}

@media (max-width: 768px) {
  h1 {
    font-size: 2.5rem;
  }
  
  .typed-wrapper {
    font-size: 1.2rem;
  }
  
  .hero-content {
    padding: 2rem;
  }
  
  .modal-container {
    max-height: 95vh;
  }
  
  .modal-body {
    padding: 1.5rem;
  }
  
  .resume-contact {
    flex-direction: column;
    gap: 0.5rem;
  }
  
  .exp-header {
    flex-direction: column;
    gap: 0.25rem;
  }
}
</style>