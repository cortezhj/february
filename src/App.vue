<script setup lang="ts">
import { ref, onMounted, computed } from 'vue'

const currentStep = ref(0)
const treeAnimationStarted = ref(false)

const totalSteps = 7

const steps = [
  {
    title: '💕',
    phrase: 'Hoy quiero dedicarte algo especial...'
  },
  {
    title: 'Mi Limonsito',
    phrase: 'Eres mi lugar favorito en todo el mundo, y mi razón para sonreír...'
  },
  {
    title: '¿Fué Cupido? No',
    phrase: 'Fue tu sonrisa. Fue tu mirada. Fue tu forma de hacerme feliz...'
  },
  {
    title: 'Recuerdos',
    phrase: 'Cada momento a tu lado es mágico e inolvidable. Cada recuerdo es un tesoro...'
  },
  {
    title: 'Feliz Día De San Valentín',
    phrase: 'Eres el WiFi de mi corazón: siempre estoy conectado contigo...'
  },
  {
    title: 'Para Ti',
    phrase: 'Eres la niña mas hermosa del mundo. Gracias por existir y por estar aqui...'
  },
  {
    title: 'Happy Day',
    phrase: 'Como este árbol, que nuestro amor siga creciendo cada día más fuerte...',
    showHeartTree: true
  }
]

const currentStepData = computed(() => steps[currentStep.value])

const nextStep = () => {
  if (currentStep.value < totalSteps - 1) {
    createHeartBurst()
    currentStep.value++
  }
}



const createHeartBurst = () => {
  const burst = document.createElement('div')
  burst.className = 'heart-burst'
  burst.style.left = '50%'
  burst.style.top = '50%'
  
  for (let i = 0; i < 15; i++) {
    const heart = document.createElement('div')
    heart.className = 'burst-heart'
    heart.textContent = '❤️'
    
    const angle = (Math.PI * 2 * i) / 15
    const distance = 100 + Math.random() * 100
    const tx = Math.cos(angle) * distance
    const ty = Math.sin(angle) * distance
    
    heart.style.setProperty('--tx', `${tx}px`)
    heart.style.setProperty('--ty', `${ty}px`)
    
    burst.appendChild(heart)
  }
  
  document.body.appendChild(burst)
  
  setTimeout(() => {
    document.body.removeChild(burst)
  }, 1500)
}

const createFloatingHearts = () => {
  const heartsContainer = document.querySelector('.hearts-background')
  if (!heartsContainer) return
  
  for (let i = 0; i < 20; i++) {
    const heart = document.createElement('div')
    heart.className = 'heart'
    heart.textContent = '❤️'
    heart.style.left = `${Math.random() * 100}%`
    heart.style.animationDelay = `${Math.random() * 8}s`
    heart.style.fontSize = `${15 + Math.random() * 20}px`
    heartsContainer.appendChild(heart)
  }
}

const createParticles = () => {
  const particlesContainer = document.querySelector('.particles')
  if (!particlesContainer) return
  
  for (let i = 0; i < 50; i++) {
    const particle = document.createElement('div')
    particle.className = 'particle'
    particle.style.left = `${Math.random() * 100}%`
    particle.style.top = `${Math.random() * 100}%`
    particle.style.animationDelay = `${Math.random() * 3}s`
    particlesContainer.appendChild(particle)
  }
}

const createHeartTree = () => {
  if (treeAnimationStarted.value) return
  treeAnimationStarted.value = true
  
  setTimeout(() => {
    const branchesContainer = document.querySelector('.tree-branches')
    if (!branchesContainer) return
    
    // Define heart positions to form a tree shape
    const treeHearts = [
      // Top (crown)
      { left: '50%', bottom: '320px', size: '25px', delay: '1.2s', color: '❤️' },
      // Second layer
      { left: '40%', bottom: '290px', size: '22px', delay: '1.3s', color: '💕' },
      { left: '60%', bottom: '290px', size: '22px', delay: '1.4s', color: '❤️' },
      // Third layer
      { left: '35%', bottom: '260px', size: '20px', delay: '1.5s', color: '💖' },
      { left: '50%', bottom: '260px', size: '23px', delay: '1.6s', color: '❤️' },
      { left: '65%', bottom: '260px', size: '20px', delay: '1.7s', color: '💕' },
      // Fourth layer
      { left: '30%', bottom: '230px', size: '18px', delay: '1.8s', color: '❤️' },
      { left: '42%', bottom: '230px', size: '21px', delay: '1.9s', color: '💖' },
      { left: '58%', bottom: '230px', size: '21px', delay: '2.0s', color: '💕' },
      { left: '70%', bottom: '230px', size: '18px', delay: '2.1s', color: '❤️' },
      // Fifth layer
      { left: '25%', bottom: '200px', size: '17px', delay: '2.2s', color: '💕' },
      { left: '37%', bottom: '200px', size: '19px', delay: '2.3s', color: '❤️' },
      { left: '50%', bottom: '200px', size: '22px', delay: '2.4s', color: '💖' },
      { left: '63%', bottom: '200px', size: '19px', delay: '2.5s', color: '❤️' },
      { left: '75%', bottom: '200px', size: '17px', delay: '2.6s', color: '💕' },
      // Sixth layer
      { left: '22%', bottom: '170px', size: '16px', delay: '2.7s', color: '❤️' },
      { left: '33%', bottom: '170px', size: '18px', delay: '2.8s', color: '💖' },
      { left: '44%', bottom: '170px', size: '20px', delay: '2.9s', color: '💕' },
      { left: '56%', bottom: '170px', size: '20px', delay: '3.0s', color: '❤️' },
      { left: '67%', bottom: '170px', size: '18px', delay: '3.1s', color: '💖' },
      { left: '78%', bottom: '170px', size: '16px', delay: '3.2s', color: '💕' },
      // Seventh layer
      { left: '20%', bottom: '140px', size: '15px', delay: '3.3s', color: '💕' },
      { left: '30%', bottom: '140px', size: '17px', delay: '3.4s', color: '❤️' },
      { left: '40%', bottom: '140px', size: '19px', delay: '3.5s', color: '💖' },
      { left: '50%', bottom: '140px', size: '21px', delay: '3.6s', color: '❤️' },
      { left: '60%', bottom: '140px', size: '19px', delay: '3.7s', color: '💖' },
      { left: '70%', bottom: '140px', size: '17px', delay: '3.8s', color: '💕' },
      { left: '80%', bottom: '140px', size: '15px', delay: '3.9s', color: '❤️' },
      // Bottom layers
      { left: '18%', bottom: '110px', size: '14px', delay: '4.0s', color: '❤️' },
      { left: '27%', bottom: '110px', size: '16px', delay: '4.1s', color: '💕' },
      { left: '36%', bottom: '110px', size: '18px', delay: '4.2s', color: '💖' },
      { left: '45%', bottom: '110px', size: '20px', delay: '4.3s', color: '❤️' },
      { left: '55%', bottom: '110px', size: '20px', delay: '4.4s', color: '💕' },
      { left: '64%', bottom: '110px', size: '18px', delay: '4.5s', color: '💖' },
      { left: '73%', bottom: '110px', size: '16px', delay: '4.6s', color: '❤️' },
      { left: '82%', bottom: '110px', size: '14px', delay: '4.7s', color: '💕' },
      // More bottom
      { left: '15%', bottom: '80px', size: '13px', delay: '4.8s', color: '💖' },
      { left: '25%', bottom: '80px', size: '15px', delay: '4.9s', color: '❤️' },
      { left: '35%', bottom: '80px', size: '17px', delay: '5.0s', color: '💕' },
      { left: '45%', bottom: '80px', size: '19px', delay: '5.1s', color: '💖' },
      { left: '55%', bottom: '80px', size: '19px', delay: '5.2s', color: '❤️' },
      { left: '65%', bottom: '80px', size: '17px', delay: '5.3s', color: '💕' },
      { left: '75%', bottom: '80px', size: '15px', delay: '5.4s', color: '💖' },
      { left: '85%', bottom: '80px', size: '13px', delay: '5.5s', color: '❤️' },
      // Base
      { left: '20%', bottom: '50px', size: '12px', delay: '5.6s', color: '💕' },
      { left: '30%', bottom: '50px', size: '14px', delay: '5.7s', color: '❤️' },
      { left: '40%', bottom: '50px', size: '16px', delay: '5.8s', color: '💖' },
      { left: '50%', bottom: '50px', size: '18px', delay: '5.9s', color: '❤️' },
      { left: '60%', bottom: '50px', size: '16px', delay: '6.0s', color: '💕' },
      { left: '70%', bottom: '50px', size: '14px', delay: '6.1s', color: '💖' },
      { left: '80%', bottom: '50px', size: '12px', delay: '6.2s', color: '❤️' }
    ]
    
    treeHearts.forEach(heart => {
      const heartEl = document.createElement('div')
      heartEl.className = 'tree-heart'
      heartEl.textContent = heart.color
      heartEl.style.left = heart.left
      heartEl.style.bottom = heart.bottom
      heartEl.style.setProperty('--heart-size', heart.size)
      heartEl.style.animationDelay = heart.delay
      branchesContainer.appendChild(heartEl)
    })
  }, 100)
}

onMounted(() => {
  createFloatingHearts()
  createParticles()
  
  // Watch for heart tree step
  const checkHeartTree = setInterval(() => {
    if (currentStep.value === totalSteps - 1 && !treeAnimationStarted.value) {
      createHeartTree()
      clearInterval(checkHeartTree)
    }
  }, 100)
})
</script>

<template>
  <div>
    <div class="hearts-background"></div>
    <div class="particles"></div>
    
    <div class="container">
      <div class="container-pattern"></div>
      <div class="progress-hearts">
        <span 
          v-for="i in totalSteps" 
          :key="i"
          class="progress-heart"
          :class="{ active: i - 1 <= currentStep }"
        >
          ❤️
        </span>
      </div>
      
      <div class="step" :key="currentStep">
        <h1 class="step-title">{{ currentStepData.title }}</h1>
        
        <p class="step-phrase">{{ currentStepData.phrase }}</p>
        

        <!-- Heart Tree Animation -->
        <div v-if="currentStepData.showHeartTree" class="heart-tree-container">
          <div class="tree-trunk"></div>
          <div class="tree-branches"></div>
        </div>
        
        <button 
          v-if="currentStep < totalSteps - 1"
          @click="nextStep"
          class="nav-button"
        >
          Sigue leyendo ❤️
        </button>
        
        <div v-else class="step-phrase" style="margin-top: 30px; font-size: 1.2rem;">
          Con todo mi corazón 💕
        </div>
      </div>
    </div>
  </div>
</template>
