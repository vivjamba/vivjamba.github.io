<template>
  <div class="hero">

  <Navbar :textLight="true"/>

  <div class="social icons">
  <a
    href="https://github.com/vivjamba"
    target="_blank"
    rel="noopener noreferrer"
    aria-label="GitHub"
  >
    <i class="fab fa-github"></i>
  </a>
  <a
    href="https://linkedin.com/in/vivien-jamba/"
    target="_blank"
    rel="noopener noreferrer"
    aria-label="LinkedIn"
  >
    <i class="fab fa-linkedin"></i>
  </a>
</div>
    <div class="content">
      <div class="intro-line">
        <span ref="vivienRef"></span>
      </div>
      <div class="typed-line">
        <span ref="beliefRef" class="belief-text"></span>
        <span class="dynamic-wrapper">
          <span ref="dynamicRef" class="dynamic"></span>
        </span>
      </div>
    </div>
      <a class="scroll-down" @click="scrollToSection">
        <span class="arrow">⌄</span>
      </a>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import Navbar from '../components/Navbar.vue'

const vivienRef = ref(null)
const beliefRef = ref(null)
const dynamicRef = ref(null)

onMounted(() => {
  const vivienText = "Hi, I'm Vivien!"
  const beliefText = 'I believe tech should be '
  let i = 0

  const typeVivien = () => {
    if (i < vivienText.length) {
      vivienRef.value.textContent += vivienText.charAt(i++)
      setTimeout(typeVivien, 60)
    } else {
      i = 0
      setTimeout(typeBelief, 600)
    }
  }

  const typeBelief = () => {
    if (i < beliefText.length) {
      beliefRef.value.textContent += beliefText.charAt(i++)
      setTimeout(typeBelief, 40)
    } else {
      setTimeout(startDynamicTyping, 800)
    }
  }

  const phrases = [
    'easy.',
    'easy to use.',
    'easy to integrate into daily life.',
    'easy to manage.',
    'for everyone.',
    'robust.',
    'built with intention.',
    'accessible to all.',
    'designed for people.',
    'adaptable.',
    'secure.',
    'made with purpose.',
    'scalable.',
  ]
  let phraseIndex = 0
  let charIndex = 0
  let isDeleting = false

  const startDynamicTyping = () => {
    const phrase = phrases[phraseIndex]
    const display = isDeleting
      ? phrase.substring(0, charIndex--)
      : phrase.substring(0, charIndex++)

    dynamicRef.value.textContent = display

    let speed = isDeleting ? 40 : 70

    if (!isDeleting && charIndex === phrase.length) {
      const delay = phraseIndex === 0 ? 1300 : 1000  
      setTimeout(() => (isDeleting = true), delay)
    }

    if (isDeleting && charIndex === 0) {
      isDeleting = false
      phraseIndex = (phraseIndex + 1) % phrases.length
    }

    setTimeout(startDynamicTyping, speed)
  }

  typeVivien()
})

const scrollToSection = () => {
  const section = document.getElementById('experience-section')
  if (section) {
    section.scrollIntoView({ behavior: 'smooth' })
  }
}
</script>

<style scoped>
.hero {
  width: 100%;
  height: 100vh;
  animation: gradient-flow 10s ease-in-out infinite;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 2rem;
  color: #ffffff;
  font-family: 'Segoe UI', sans-serif;
  position: relative;
  overflow: hidden;
}

.hero::before {
  content: '';
  position: absolute;
  inset: -100%;
  background: conic-gradient(from 0deg at top left,rgb(26, 105, 202), #13218a);
  animation: spin-gradient 20s linear infinite;
  z-index: -2;
}

.hero::after {
  content: '';
  position: absolute;
  inset: 0;
  pointer-events: none;
  z-index: -1;
  background:
    radial-gradient(circle, rgba(171, 223, 255, 0.03) 0%, transparent 80%) 20% 30% / 400px 100px,
    radial-gradient(circle, rgba(171, 223, 255, 0.03) 0%, transparent 40%) 70% 40% / 200px 100px,
    radial-gradient(circle, rgba(171, 223, 255, 0.01) 0%, transparent 80%) 60% 25% / 1000px 20px,
    radial-gradient(circle, rgba(255, 255, 255, 0.03) 0%, transparent 80%) 40% 70% / 1000px 1000px,
    radial-gradient(circle, rgba(255, 255, 255, 0.02) 0%, transparent 40%) 40% 70% / 600px 100px;
  background-repeat: repeat;
  animation:
    cloud-drift 50s linear infinite,
    cloud-pulse 5s ease-in-out infinite alternate;
}

@keyframes spin-gradient {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}

@keyframes cloud-drift {
  0% { background-position: 0% 0%, 0% 0%, 0% 0%, 0% 0%; }  
  50% { background-position: 100% 100%, 100% 100%, 100% 100%, 100% 100%; }
  100% { background-position: 0% 0%, 0% 0%, 0% 0%, 0% 0%; }  
}

@keyframes cloud-pulse {
  0%, 100% {
    background-size: 20.8% 20.8%, 27.8% 27.8%, 34.7% 34.7%, 24.3% 24.3%;
  }
  50% {
    background-size: 22.9% 22.9%, 30.6% 30.6%, 37.5% 37.5%, 26.7% 26.7%;
  }
}


.content {
  width: 100%;
  max-width: 800px;
  margin: 0 auto 0 auto;
  padding-left: 7rem;
  text-align: left;
}

.intro-line {
  font-size: 5rem;
  font-weight: 700;
  margin-bottom: 1rem;
  white-space: nowrap;
}

.typed-line {
  font-size: 1.5rem;
  font-weight: 400;
  display: flex;
  align-items: center;
  flex-wrap: nowrap;
  gap: 0.5ch;
  white-space: nowrap;
}

.belief-text {
  flex-shrink: 0;
}

.dynamic-wrapper {
  display: inline-block;
  min-width: 18ch;
  text-align: left;
}

.dynamic {
  border-right: 2px solid white;
  animation: blink-caret 1s step-end infinite;
}

@keyframes blink-caret {
  0%, 100% { border-color: transparent; }
  50% { border-color: white; }
}

.scroll-down {
  position: absolute;
  bottom: 20px;
  left: 50%;
  transform: translateX(-50%);
  cursor: pointer; 
}


.arrow {
  display: inline-block;
  font-size: 3rem;
  color: white;
  animation: bounce 1.6s ease-in-out infinite;
  will-change: transform;
}

@keyframes bounce {
  0%, 100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(10px);
  }
}

.social {
  position: absolute;
  top: 1.5rem;
  right: 2rem;
  z-index: 10;
  display: flex;
  gap: 1.2rem;
}

.nav {
  position: absolute;
  top: 1.5rem;
  left: 2rem;
  z-index: 10;
  display: flex;
  gap: 1.2rem;
}

.icons a {
  color: white;
  font-size: 2.8rem;
  transition: opacity 0.3s ease;
}

.icons a:hover {
  opacity: 0.7;
}

.nav-text-links {
  position: absolute;
  top: 1.5rem;
  left: 2rem;
  z-index: 10;
  display: flex;
  gap: 1.8rem;
}

.nav-text-links a {
  color: white;
  font-size: 1.4rem;
  font-weight: 500;
  padding: 0.4rem 0.8rem;
  border-radius: 6px;
  transition: background-color 0.3s ease, opacity 0.3s ease;
  text-decoration: none;
  cursor: pointer;
}

.nav-text-links a:hover {
  background-color: rgba(255, 255, 255, 0.15);
  opacity: 0.85;
}



@media (max-width: 768px) {
  .content {
    padding-left: .5rem;
    text-align: center;
  }

  .intro-line {
    font-size: 2rem;
    white-space: normal;
  }

  .typed-line {
    font-size: 1rem;
    flex-wrap: wrap;
    justify-content: center;
    text-align: center;
  }

  .nav-text-links a {
    font-size: 0rem;
  } 

  .social {
    top: 4rem;
    right: 50%;
    transform: translateX(50%);
    gap: 1rem;
  }

  .icons a {
    font-size: 2rem;
  }


  .arrow {
    font-size: 2rem;
  }
}

</style>
