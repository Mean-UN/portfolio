<template>
  <section class="relative min-h-screen flex items-center justify-center overflow-hidden">
    <!-- Animated Background -->
    <div class="absolute inset-0 bg-gradient-to-br from-blue-50 via-white to-cyan-50">
      <!-- Floating Elements -->
      <div class="absolute top-20 left-10 w-20 h-20 bg-blue-200/30 rounded-full blur-xl animate-float"></div>
      <div class="absolute top-40 right-20 w-32 h-32 bg-cyan-200/20 rounded-full blur-xl animate-float-delayed"></div>
      <div class="absolute bottom-40 left-20 w-24 h-24 bg-purple-200/25 rounded-full blur-xl animate-float-slow"></div>
      
      <!-- Grid Pattern -->
      <div class="absolute inset-0 opacity-5">
        <div class="grid grid-cols-12 gap-4 h-full">
          <div v-for="i in 12" :key="i" class="border-r border-gray-300"></div>
        </div>
      </div>
    </div>

    <!-- Main Content -->
    <div class="relative z-10 text-center px-6 pt-20 pb-10 max-w-4xl mx-auto">
      <!-- Profile Image -->
      <div class="mb-8" ref="profileSection">
        <div class="relative inline-block">
          <div class="w-32 h-32 mx-auto rounded-full bg-gradient-to-r from-blue-500 to-cyan-500 p-1 shadow-2xl">
            <div class="w-full h-full rounded-full bg-white flex items-center justify-center">
              <img 
                src="@/assets/images/avatar.png" 
                alt="Mean's Profile"
                class="w-28 h-28 rounded-full object-cover"
              />
            </div>
          </div>
          <!-- Status Indicator -->
          <div class="absolute bottom-2 right-2 w-6 h-6 bg-green-500 rounded-full border-4 border-white shadow-lg animate-pulse"></div>
        </div>
      </div>

      <!-- Main Heading -->
      <div ref="headingSection">
        <h1 class="text-4xl md:text-6xl lg:text-7xl font-bold text-gray-800 mb-6 leading-tight">
          Hello, I'm 
          <span class="relative inline-block">
            <span class="bg-gradient-to-r from-blue-600 via-purple-600 to-cyan-600 bg-clip-text text-transparent animate-gradient">
              Mean
            </span>
            <div class="absolute -bottom-2 left-0 w-full h-1 bg-gradient-to-r from-blue-600 to-cyan-600 rounded-full transform scale-x-0 animate-underline"></div>
          </span>
        </h1>
      </div>

      <!-- Typed Text -->
      <div ref="typedSection" class="mb-8">
        <h2 class="text-2xl md:text-4xl font-semibold text-gray-600 h-12 md:h-16 flex items-center justify-center">
          <span ref="typedText" class=""></span>
        </h2>
      </div>

      <!-- Description -->
      <div ref="descriptionSection">
        <p class="text-lg md:text-xl text-gray-600 max-w-2xl mx-auto mb-8 leading-relaxed">
          I'm passionate about building 
          <span class="font-semibold text-blue-600">full-stack web applications</span> 
          and designing 
          <span class="font-semibold text-cyan-600">user-friendly experiences</span> 
          that make a difference.
        </p>
      </div>

      <!-- Action Buttons -->
      <div ref="buttonsSection" class="flex flex-col sm:flex-row gap-4 justify-center items-center">
        <RouterLink
          to="/projects"
          class="group relative px-8 py-4 bg-gradient-to-r from-blue-600 to-cyan-600 text-white font-semibold rounded-full shadow-lg hover:shadow-xl transform hover:-translate-y-1 transition-all duration-300 overflow-hidden"
        >
          <span class="relative z-10 flex items-center">
            View My Work
            <svg class="w-5 h-5 ml-2 transition-transform group-hover:translate-x-1" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8l4 4m0 0l-4 4m4-4H3" />
            </svg>
          </span>
          <div class="absolute inset-0 bg-gradient-to-r from-cyan-600 to-blue-600 opacity-0 group-hover:opacity-100 transition-opacity duration-300"></div>
        </RouterLink>

        <RouterLink
          to="/contact"
          class="group px-8 py-4 border-2 border-blue-600 text-blue-600 font-semibold rounded-full hover:bg-blue-600 hover:text-white transition-all duration-300 transform hover:-translate-y-1"
        >
          <span class="flex items-center">
            Get In Touch
            <svg class="w-5 h-5 ml-2 transition-transform group-hover:rotate-12" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 4.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z" />
            </svg>
          </span>
        </RouterLink>
      </div>

      <!-- Social Links -->
      <div ref="socialSection" class="mt-12 flex justify-center space-x-6">
        <a 
          v-for="social in socialLinks" 
          :key="social.name"
          :href="social.url" 
          target="_blank" 
          rel="noopener noreferrer"
          class="group w-12 h-12 bg-white rounded-full shadow-lg hover:shadow-xl flex items-center justify-center transition-all duration-300 transform hover:-translate-y-1 hover:scale-110"
          :class="social.hoverColor"
          v-html="social.icon"
        >
        </a>
      </div>

      <!-- Scroll Indicator -->
      <!-- <div class="absolute bottom-8 left-1/2 transform -translate-x-1/2 animate-bounce">
        <div class="w-6 h-10 border-2 border-gray-400 rounded-full flex justify-center">
          <div class="w-1 h-3 bg-gray-400 rounded-full mt-2 animate-pulse"></div>
        </div>
      </div> -->
    </div>
  </section>
</template>

<script setup>
import { onMounted, ref, onUnmounted } from 'vue'
import { RouterLink } from 'vue-router'
import Typed from 'typed.js'
import ScrollReveal from 'scrollreveal'

// Template refs
const typedText = ref(null)
const profileSection = ref(null)
const headingSection = ref(null)
const typedSection = ref(null)
const descriptionSection = ref(null)
const buttonsSection = ref(null)
const socialSection = ref(null)

// Typed.js instance
let typed = null

// Social media links with inline SVG icons
const socialLinks = [
  {
    name: 'GitHub',
    url: 'https://github.com/Mean-UN',
    hoverColor: 'hover:bg-gray-800',
    icon: `<svg fill="currentColor" viewBox="0 0 24 24" class="w-6 h-6">
      <path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/>
    </svg>`
  },
  {
    name: 'LinkedIn',
    url: 'linkedin.com/in/mean-un-personal',
    hoverColor: 'hover:bg-blue-600',
    icon: `<svg fill="currentColor" viewBox="0 0 24 24" class="w-6 h-6">
      <path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/>
    </svg>`
  },
  {
    name: 'Twitter',
    url: 'https://x.com/Un_Mean168',
    hoverColor: 'hover:bg-blue-400',
    icon: `<svg fill="currentColor" viewBox="0 0 24 24" class="w-6 h-6">
      <path d="M23.953 4.57a10 10 0 01-2.825.775 4.958 4.958 0 002.163-2.723c-.951.555-2.005.959-3.127 1.184a4.92 4.92 0 00-8.384 4.482C7.69 8.095 4.067 6.13 1.64 3.162a4.822 4.822 0 00-.666 2.475c0 1.71.87 3.213 2.188 4.096a4.904 4.904 0 01-2.228-.616v.06a4.923 4.923 0 003.946 4.827 4.996 4.996 0 01-2.212.085 4.936 4.936 0 004.604 3.417 9.867 9.867 0 01-6.102 2.105c-.39 0-.779-.023-1.17-.067a13.995 13.995 0 007.557 2.209c9.053 0 13.998-7.496 13.998-13.985 0-.21 0-.42-.015-.63A9.935 9.935 0 0024 4.59z"/>
    </svg>`
  },
  {
    name: 'Email',
    url: 'mailto:mean.un@student.passerellesnumeriques.org',
    hoverColor: 'hover:bg-red-500',
    icon: `<svg fill="none" stroke="currentColor" viewBox="0 0 24 24" class="w-6 h-6">
      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 4.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"/>
    </svg>`
  }
]

onMounted(() => {
  // Initialize Typed.js
  typed = new Typed(typedText.value, {
    strings: [
      'a Full-Stack Developer.',
      'a Web Developer.' ,
      'a Front-End Developer.',
      'a Back-End Developer.',
      'a Mobile Developer.',
      'a Student at Passerelles numériques Cambodia.',
    ],
    typeSpeed: 80,
    backSpeed: 40,
    backDelay: 2000,
    startDelay: 1000,
    loop: true,
    showCursor: true,
    cursorChar: '|',
  })

  // Initialize ScrollReveal
  const sr = ScrollReveal({
    origin: 'bottom',
    distance: '60px',
    duration: 1000,
    delay: 100,
    reset: false,
    easing: 'cubic-bezier(0.5, 0, 0, 1)',
  })

  // Reveal animations with staggered delays
  sr.reveal(profileSection.value, { delay: 200 })
  sr.reveal(headingSection.value, { delay: 400 })
  sr.reveal(typedSection.value, { delay: 600 })
  sr.reveal(descriptionSection.value, { delay: 800 })
  sr.reveal(buttonsSection.value, { delay: 1000 })
  sr.reveal(socialSection.value, { delay: 1200 })
})

onUnmounted(() => {
  // Clean up Typed.js instance
  if (typed) {
    typed.destroy()
  }
})
</script>

<style scoped>
/* Custom animations */
@keyframes float {
  0%, 100% { transform: translateY(0px) rotate(0deg); }
  50% { transform: translateY(-20px) rotate(180deg); }
}

@keyframes float-delayed {
  0%, 100% { transform: translateY(0px) rotate(0deg); }
  50% { transform: translateY(-30px) rotate(-180deg); }
}

@keyframes float-slow {
  0%, 100% { transform: translateY(0px) rotate(0deg); }
  50% { transform: translateY(-15px) rotate(90deg); }
}

@keyframes gradient {
  0%, 100% { background-position: 0% 50%; }
  50% { background-position: 100% 50%; }
}

@keyframes underline {
  0% { transform: scaleX(0); }
  100% { transform: scaleX(1); }
}

.animate-float {
  animation: float 6s ease-in-out infinite;
}

.animate-float-delayed {
  animation: float-delayed 8s ease-in-out infinite;
}

.animate-float-slow {
  animation: float-slow 10s ease-in-out infinite;
}

.animate-gradient {
  background-size: 200% 200%;
  animation: gradient 3s ease infinite;
}

.animate-underline {
  animation: underline 1s ease-out 2s forwards;
}

/* Responsive text sizing */
@media (max-width: 640px) {
  h1 {
    font-size: 2.5rem;
    line-height: 1.2;
  }
  
  h2 {
    font-size: 1.5rem;
  }
}

/* Custom scrollbar */
::-webkit-scrollbar {
  width: 8px;
}

::-webkit-scrollbar-track {
  background: #f1f1f1;
}

::-webkit-scrollbar-thumb {
  background: linear-gradient(to bottom, #3b82f6, #06b6d4);
  border-radius: 4px;
}

::-webkit-scrollbar-thumb:hover {
  background: linear-gradient(to bottom, #2563eb, #0891b2);
}
</style>