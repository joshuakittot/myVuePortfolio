<!-- src/App.vue -->
<template>
  <div class="app">
    <canvas ref="canvasRef" class="code-background"></canvas>
    
    <main>
      <Hero />
      <About />
      <Skills />
      <Projects />
      <Contact />
    </main>
    
    <footer class="footer">
      <div class="container">
        <p>© 2026 Joshua Kittot | Built with Vue & ☕</p>
      </div>
    </footer>
  </div>
</template>

<script setup>
import { onMounted, onUnmounted, ref } from 'vue'
import Hero from './Components/Hero.vue'
import About from './Components/About.vue'
import Skills from './Components/Skills.vue'
import Projects from './Components/Projects.vue'
import Contact from './Components/Contact.vue'

const canvasRef = ref(null)
let animationId = null
let ctx = null
let particles = []
let width = 0, height = 0

const initCanvas = () => {
  const canvas = canvasRef.value
  if (!canvas) return
  
  ctx = canvas.getContext('2d')
  
  const resize = () => {
    width = window.innerWidth
    height = window.innerHeight
    canvas.width = width
    canvas.height = height
  }
  
  window.addEventListener('resize', resize)
  resize()
  
  // Code characters to rain
  const chars = '01ABCDEFGHIJKLMNOPQRSTUVWXYZ{}[]();:<>/?!@#$%^&*'
  
  class Particle {
    constructor() {
      this.x = Math.random() * width
      this.y = Math.random() * height - height
      this.char = chars[Math.floor(Math.random() * chars.length)]
      this.speed = 1 + Math.random() * 3
      this.opacity = 0.2 + Math.random() * 0.5
      this.size = 12 + Math.random() * 8
    }
    
    update() {
      this.y += this.speed
      if (this.y > height) {
        this.y = -20
        this.x = Math.random() * width
        this.char = chars[Math.floor(Math.random() * chars.length)]
      }
    }
    
    draw() {
      if (!ctx) return
      ctx.font = `${this.size}px 'Fira Code', 'Courier New', monospace`
      ctx.fillStyle = `rgba(59, 130, 246, ${this.opacity * 0.6})`
      ctx.fillText(this.char, this.x, this.y)
    }
  }
  
  // Initialize particles
  for (let i = 0; i < 150; i++) {
    particles.push(new Particle())
  }
  
  const animate = () => {
    if (!ctx || !canvas) return
    
    // Fade effect for trailing
    ctx.fillStyle = 'rgba(10, 10, 15, 0.05)'
    ctx.fillRect(0, 0, width, height)
    
    particles.forEach(particle => {
      particle.update()
      particle.draw()
    })
    
    animationId = requestAnimationFrame(animate)
  }
  
  animate()
}

onMounted(() => {
  initCanvas()
})

onUnmounted(() => {
  if (animationId) {
    cancelAnimationFrame(animationId)
  }
})
</script>

<style scoped>
.app {
  position: relative;
  min-height: 100vh;
}

.code-background {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 0;
  pointer-events: none;
}

main {
  position: relative;
  z-index: 1;
}

.footer {
  position: relative;
  z-index: 2;
  text-align: center;
  padding: 2rem 0;
  background: rgba(10, 10, 15, 0.8);
  backdrop-filter: blur(10px);
  border-top: 1px solid rgba(59, 130, 246, 0.2);
  font-size: 0.9rem;
  color: #a1a1aa;
}
</style>