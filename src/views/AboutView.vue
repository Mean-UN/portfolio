<template>
  <section class="min-h-screen bg-gradient-to-br from-gray-50 to-blue-50 py-20 px-6">
    <div class="max-w-6xl mx-auto">
      <!-- Header -->
      <div class="text-center mb-16" ref="headerSection">
        <h1 class="text-4xl md:text-5xl font-bold text-gray-800 mb-4">
          About <span class="text-blue-600">Mean Un</span>
        </h1>
        <p class="text-xl text-gray-600 mb-4">Junior Web Developer</p>
        <div class="w-24 h-1 bg-gradient-to-r from-blue-600 to-cyan-600 mx-auto rounded-full"></div>
      </div>

      <!-- Main Content -->
      <div class="grid lg:grid-cols-2 gap-12 items-start">
        <!-- Left Column - About Info -->
        <div class="space-y-8" ref="aboutSection">
          <!-- Personal Information -->
          <div class="bg-white rounded-2xl shadow-lg p-8 hover:shadow-xl transition-shadow duration-300">
            <h3 class="text-2xl font-bold text-gray-800 mb-6 flex items-center">
              <div class="w-8 h-8 bg-blue-600 rounded-full flex items-center justify-center mr-3">
                <svg class="w-4 h-4 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M16 7a4 4 0 11-8 0 4 4 0 018 0zM12 14a7 7 0 00-7 7h14a7 7 0 00-7-7z" />
                </svg>
              </div>
              Personal Information
            </h3>
            
            <div class="grid md:grid-cols-2 gap-4 mb-6">
              <div class="flex items-center space-x-3">
                <div class="w-10 h-10 bg-blue-100 rounded-full flex items-center justify-center">
                  <svg class="w-5 h-5 text-blue-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M16 7a4 4 0 11-8 0 4 4 0 018 0zM12 14a7 7 0 00-7 7h14a7 7 0 00-7-7z" />
                  </svg>
                </div>
                <div>
                  <p class="text-sm text-gray-500">Name</p>
                  <p class="font-semibold text-gray-800">Un Mean</p>
                </div>
              </div>
              
              <div class="flex items-center space-x-3">
                <div class="w-10 h-10 bg-green-100 rounded-full flex items-center justify-center">
                  <svg class="w-5 h-5 text-green-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 7V3a2 2 0 012-2h4a2 2 0 012 2v4m-6 0V6a2 2 0 012-2h4a2 2 0 012 2v1m-6 0h6m-6 0l-.5 3.5A2 2 0 005.5 13H18.5a2 2 0 001.5-1.5L19.5 7m-13 0h13" />
                  </svg>
                </div>
                <div>
                  <p class="text-sm text-gray-500">Birth Date</p>
                  <p class="font-semibold text-gray-800">May 24, 2004</p>
                </div>
              </div>
              
              <div class="flex items-center space-x-3">
                <div class="w-10 h-10 bg-purple-100 rounded-full flex items-center justify-center">
                  <svg class="w-5 h-5 text-purple-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z" />
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z" />
                  </svg>
                </div>
                <div>
                  <p class="text-sm text-gray-500">Location</p>
                  <p class="font-semibold text-gray-800">Phnom Penh, Cambodia</p>
                </div>
              </div>
              
              <div class="flex items-center space-x-3">
                <div class="w-10 h-10 bg-orange-100 rounded-full flex items-center justify-center">
                  <svg class="w-5 h-5 text-orange-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z" />
                  </svg>
                </div>
                <div>
                  <p class="text-sm text-gray-500">Phone</p>
                  <p class="font-semibold text-gray-800">+855 97 920 1500</p>
                </div>
              </div>
            </div>

            <p class="text-gray-600 leading-relaxed text-lg mb-8">
              I am a passionate Junior Web Developer currently pursuing an Associate Degree at 
              <span class="font-semibold text-blue-600">Passerelles numériques Cambodia (PNC)</span> 
              through a competitive scholarship program. I specialize in full-stack web development with expertise in 
              <span class="font-semibold text-green-600">PHP, Laravel, JavaScript, Vue.js</span>, and modern web technologies.
            </p>
            
            <!-- Stats -->
            <div class="grid grid-cols-3 gap-4 mb-8">
              <div class="text-center p-4 bg-blue-50 rounded-lg">
                <div class="text-2xl font-bold text-blue-600">9+</div>
                <div class="text-sm text-gray-600">Projects Completed</div>
              </div>
              <div class="text-center p-4 bg-green-50 rounded-lg">
                <div class="text-2xl font-bold text-green-600">1.5+</div>
                <div class="text-sm text-gray-600">Years Learning</div>
              </div>
              <div class="text-center p-4 bg-purple-50 rounded-lg">
                <div class="text-2xl font-bold text-purple-600">15+</div>
                <div class="text-sm text-gray-600">Technologies</div>
              </div>
            </div>

            <!-- Download CV Button -->
            <button 
              @click="downloadCV"
              class="group w-full sm:w-auto bg-gradient-to-r from-blue-600 to-cyan-600 text-white font-semibold py-4 px-8 rounded-full shadow-lg hover:shadow-xl transform hover:-translate-y-1 transition-all duration-300 flex items-center justify-center"
            >
              <span class="mr-2">Download CV</span>
              <svg class="w-5 h-5 transition-transform group-hover:translate-y-1" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 10v6m0 0l-3-3m3 3l3-3m2 8H7a2 2 0 01-2-2V5a2 2 0 012-2h5.586a1 1 0 01.707.293l5.414 5.414a1 1 0 01.293.707V19a2 2 0 01-2 2z" />
              </svg>
            </button>
          </div>

          <!-- Education -->
          <div class="bg-white rounded-2xl shadow-lg p-8 hover:shadow-xl transition-shadow duration-300">
            <h3 class="text-2xl font-bold text-gray-800 mb-6 flex items-center">
              <div class="w-8 h-8 bg-green-600 rounded-full flex items-center justify-center mr-3">
                <svg class="w-4 h-4 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 14l9-5-9-5-9 5 9 5z" />
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 14l6.16-3.422a12.083 12.083 0 01.665 6.479A11.952 11.952 0 0012 20.055a11.952 11.952 0 00-6.824-2.998 12.078 12.078 0 01.665-6.479L12 14z" />
                </svg>
              </div>
              Education
            </h3>
            
            <div class="space-y-6">
              <div class="border-l-4 border-blue-500 pl-6">
                <div class="flex justify-between items-start mb-2">
                  <h4 class="text-lg font-semibold text-gray-800">Associate Degree</h4>
                  <span class="text-sm text-gray-500 bg-blue-100 px-3 py-1 rounded-full">2024 - Present</span>
                </div>
                <p class="text-blue-600 font-medium mb-2">Passerelles numériques Cambodia (PNC)</p>
                <p class="text-gray-600 text-sm">Competitive scholarship program focusing on Web Programming, English, and Personal Development</p>
              </div>
              
              <div class="border-l-4 border-green-500 pl-6">
                <div class="flex justify-between items-start mb-2">
                  <h4 class="text-lg font-semibold text-gray-800">High School Diploma</h4>
                  <span class="text-sm text-gray-500 bg-green-100 px-3 py-1 rounded-full">2021 - 2023</span>
                </div>
                <p class="text-green-600 font-medium mb-2">Triel High School</p>
                <p class="text-gray-600 text-sm">Successfully passed Grade 12 National Exam (Bac II)</p>
              </div>
            </div>
          </div>
        </div>

        <!-- Right Column - Skills -->
        <div class="space-y-6" ref="skillsSection">
          <!-- Frontend Skills -->
          <div class="bg-white rounded-2xl shadow-lg p-8 hover:shadow-xl transition-all duration-300 transform hover:-translate-y-1">
            <div class="flex items-center mb-6">
              <div class="w-10 h-10 bg-gradient-to-r from-orange-500 to-red-500 rounded-full flex items-center justify-center mr-4">
                <svg class="w-5 h-5 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9.75 17L9 20l-1 1h8l-1-1-.75-3M3 13h18M5 17h14a2 2 0 002-2V5a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z" />
                </svg>
              </div>
              <h3 class="text-xl font-bold text-gray-800">Frontend Technologies</h3>
            </div>
            <div class="flex flex-wrap gap-3">
              <span 
                v-for="skill in frontendSkills" 
                :key="skill.name"
                class="px-4 py-2 rounded-full text-sm font-medium transition-all duration-300 hover:scale-105"
                :class="skill.color"
              >
                {{ skill.name }}
              </span>
            </div>
          </div>

          <!-- Backend Skills -->
          <div class="bg-white rounded-2xl shadow-lg p-8 hover:shadow-xl transition-all duration-300 transform hover:-translate-y-1">
            <div class="flex items-center mb-6">
              <div class="w-10 h-10 bg-gradient-to-r from-green-500 to-emerald-500 rounded-full flex items-center justify-center mr-4">
                <svg class="w-5 h-5 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 12h14M5 12a2 2 0 01-2-2V6a2 2 0 012-2h14a2 2 0 012 2v4a2 2 0 01-2 2M5 12a2 2 0 00-2 2v4a2 2 0 002 2h14a2 2 0 002-2v-4a2 2 0 00-2-2m-2-4h.01M17 16h.01" />
                </svg>
              </div>
              <h3 class="text-xl font-bold text-gray-800">Backend & Server</h3>
            </div>
            <div class="flex flex-wrap gap-3">
              <span 
                v-for="skill in backendSkills" 
                :key="skill.name"
                class="px-4 py-2 rounded-full text-sm font-medium transition-all duration-300 hover:scale-105"
                :class="skill.color"
              >
                {{ skill.name }}
              </span>
            </div>
          </div>

          <!-- Database & Tools -->
          <div class="bg-white rounded-2xl shadow-lg p-8 hover:shadow-xl transition-all duration-300 transform hover:-translate-y-1">
            <div class="flex items-center mb-6">
              <div class="w-10 h-10 bg-gradient-to-r from-purple-500 to-indigo-500 rounded-full flex items-center justify-center mr-4">
                <svg class="w-5 h-5 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 7v10c0 2.21 3.582 4 8 4s8-1.79 8-4V7M4 7c0 2.21 3.582 4 8 4s8-1.79 8-4M4 7c0-2.21 3.582-4 8-4s8 1.79 8 4m0 5c0 2.21-3.582 4-8 4s-8-1.79-8-4" />
                </svg>
              </div>
              <h3 class="text-xl font-bold text-gray-800">Database & Tools</h3>
            </div>
            <div class="flex flex-wrap gap-3">
              <span 
                v-for="skill in databaseSkills" 
                :key="skill.name"
                class="px-4 py-2 rounded-full text-sm font-medium transition-all duration-300 hover:scale-105"
                :class="skill.color"
              >
                {{ skill.name }}
              </span>
            </div>
          </div>

          <!-- Languages -->
          <div class="bg-white rounded-2xl shadow-lg p-8 hover:shadow-xl transition-all duration-300 transform hover:-translate-y-1">
            <div class="flex items-center mb-6">
              <div class="w-10 h-10 bg-gradient-to-r from-pink-500 to-rose-500 rounded-full flex items-center justify-center mr-4">
                <svg class="w-5 h-5 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 5h12M9 3v2m1.048 9.5A18.022 18.022 0 016.412 9m6.088 9h7M11 21l5-10 5 10M12.751 5C11.783 10.77 8.07 15.61 3 18.129" />
                </svg>
              </div>
              <h3 class="text-xl font-bold text-gray-800">Languages</h3>
            </div>
            <div class="space-y-4">
              <div class="flex justify-between items-center">
                <span class="font-medium text-gray-800">Khmer</span>
                <span class="text-sm bg-green-100 text-green-800 px-3 py-1 rounded-full">Native</span>
              </div>
              <div class="flex justify-between items-center">
                <span class="font-medium text-gray-800">English</span>
                <span class="text-sm bg-blue-100 text-blue-800 px-3 py-1 rounded-full">Pre-Intermediate</span>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- Recent Projects Highlight -->
      <div class="mt-20" ref="projectsSection">
        <div class="text-center mb-12">
          <h2 class="text-3xl font-bold text-gray-800 mb-4">Recent Projects</h2>
          <p class="text-gray-600 max-w-2xl mx-auto">
            Here are some of my recent projects that showcase my skills and learning journey.
          </p>
        </div>

        <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
          <div 
            v-for="project in recentProjects" 
            :key="project.title"
            class="bg-white rounded-2xl shadow-lg p-6 hover:shadow-xl transition-all duration-300 transform hover:-translate-y-2"
          >
            <div class="w-12 h-12 mb-4 rounded-full flex items-center justify-center" :class="project.bgColor">
              <div v-html="project.icon" class="w-6 h-6 text-white"></div>
            </div>
            <h3 class="text-xl font-bold text-gray-800 mb-3">{{ project.title }}</h3>
            <p class="text-gray-600 mb-4">{{ project.description }}</p>
            <div class="flex flex-wrap gap-2">
              <span 
                v-for="tech in project.technologies" 
                :key="tech"
                class="px-2 py-1 text-xs bg-gray-100 text-gray-700 rounded-md"
              >
                {{ tech }}
              </span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { onMounted, ref } from 'vue'
import ScrollReveal from 'scrollreveal'

// Template refs
const headerSection = ref(null)
const aboutSection = ref(null)
const skillsSection = ref(null)
const projectsSection = ref(null)

// Skills data based on your CV
const frontendSkills = [
  { name: 'HTML/CSS', color: 'bg-orange-100 text-orange-800 hover:bg-orange-200' },
  { name: 'SASS', color: 'bg-pink-100 text-pink-800 hover:bg-pink-200' },
  { name: 'JavaScript', color: 'bg-yellow-100 text-yellow-800 hover:bg-yellow-200' },
  { name: 'TypeScript', color: 'bg-blue-100 text-blue-800 hover:bg-blue-200' },
  { name: 'Vue.js', color: 'bg-green-100 text-green-800 hover:bg-green-200' },
  { name: 'Bootstrap', color: 'bg-purple-100 text-purple-800 hover:bg-purple-200' },
  { name: 'Tailwind CSS', color: 'bg-blue-100 text-blue-800 hover:bg-blue-200' },
  { name: 'Dart', color: 'bg-pink-100 text-pink-800 hover:bg-pink-200' },
]

const backendSkills = [
  { name: 'PHP', color: 'bg-indigo-100 text-indigo-800 hover:bg-indigo-200' },
  { name: 'Laravel', color: 'bg-red-100 text-red-800 hover:bg-red-200' },
  { name: 'Node.js', color: 'bg-green-100 text-green-800 hover:bg-green-200' },
  { name: 'Python', color: 'bg-blue-100 text-blue-800 hover:bg-blue-200' },
  { name: 'REST API', color: 'bg-cyan-100 text-cyan-800 hover:bg-cyan-200' },
  { name: 'OOP', color: 'bg-purple-100 text-purple-800 hover:bg-purple-200' }
]

const databaseSkills = [
  { name: 'MySQL', color: 'bg-blue-100 text-blue-800 hover:bg-blue-200' },
  { name: 'Firebase', color: 'bg-orange-100 text-orange-800 hover:bg-orange-200' },
  { name: 'GitHub', color: 'bg-gray-100 text-gray-800 hover:bg-gray-200' },
  { name: 'AWS EC2', color: 'bg-yellow-100 text-yellow-800 hover:bg-yellow-200' },
  { name: 'Linux Ubuntu', color: 'bg-orange-100 text-orange-800 hover:bg-orange-200' },
  { name: 'WordPress', color: 'bg-blue-100 text-blue-800 hover:bg-blue-200' },
  { name: 'Figma', color: 'bg-purple-100 text-purple-800 hover:bg-purple-200' },
  { name: 'Jira', color: 'bg-blue-100 text-blue-800 hover:bg-blue-200' },
  { name: 'Postman', color: 'bg-orange-100 text-orange-800 hover:bg-orange-200' }
]

// Recent projects based on your CV
const recentProjects = [
  {
    title: 'Booking Travel APP',
    description: 'Seft learning to create a app system for booking room in hotel with adventure place that user want to go and travel with their family or friends.',
    technologies: ['Flutter', 'Dart', 'Laravel', 'MySQL', 'Jira', 'Git'],
    icon: `<svg fill="currentColor" viewBox="0 0 24 24"><path d="M7 18c-1.1 0-2 .9-2 2s.9 2 2 2 2-.9 2-2-.9-2-2-2zM1 2v2h2l3.6 7.59-1.35 2.45c-.16.28-.25.61-.25.96 0 1.1.9 2 2 2h12v-2H7.42c-.14 0-.25-.11-.25-.25l.03-.12L8.1 13h7.45c.75 0 1.41-.41 1.75-1.03L21.7 4H5.21l-.94-2H1zm16 16c-1.1 0-2 .9-2 2s.9 2 2 2 2-.9 2-2-.9-2-2-2z"/></svg>`,
    bgColor: 'bg-gradient-to-r from-blue-500 to-cyan-500'
  },
  {
    title: 'Beauty Store System',
    description: 'Full-stack e-commerce website with AWS deployment, user management, and Telegram integration.',
    technologies: ['HTML', 'CSS', 'JS', 'Bootstrap', 'PHP', 'MySQL', 'AWS'],
    icon: `<svg fill="currentColor" viewBox="0 0 24 24"><path d="M7 18c-1.1 0-2 .9-2 2s.9 2 2 2 2-.9 2-2-.9-2-2-2zM1 2v2h2l3.6 7.59-1.35 2.45c-.16.28-.25.61-.25.96 0 1.1.9 2 2 2h12v-2H7.42c-.14 0-.25-.11-.25-.25l.03-.12L8.1 13h7.45c.75 0 1.41-.41 1.75-1.03L21.7 4H5.21l-.94-2H1zm16 16c-1.1 0-2 .9-2 2s.9 2 2 2 2-.9 2-2-.9-2-2-2z"/></svg>`,
    bgColor: 'bg-gradient-to-r from-blue-500 to-cyan-500'
  },
  {
    title: 'Expense Management App',
    description: 'Responsive web application for managing personal expenses with CRUD functionality.',
    technologies: ['HTML', 'CSS', 'JavaScript'],
    icon: `<svg fill="currentColor" viewBox="0 0 24 24"><path d="M11.8 10.9c-2.27-.59-3-1.2-3-2.15 0-1.09 1.01-1.85 2.7-1.85 1.78 0 2.44.85 2.5 2.1h2.21c-.07-1.72-1.12-3.3-3.21-3.81V3h-3v2.16c-1.94.42-3.5 1.68-3.5 3.61 0 2.31 1.91 3.46 4.7 4.13 2.5.6 3 1.48 3 2.41 0 .69-.49 1.79-2.7 1.79-2.06 0-2.87-.92-2.98-2.1h-2.2c.12 2.19 1.76 3.42 3.68 3.83V21h3v-2.15c1.95-.37 3.5-1.5 3.5-3.55 0-2.84-2.43-3.81-4.7-4.4z"/></svg>`,
    bgColor: 'bg-gradient-to-r from-green-500 to-emerald-500'
  },
  {
    title: 'Music Voice Controller',
    description: 'Python-based voice-controlled music application using Tkinter for the user interface.',
    technologies: ['Python', 'Tkinter'],
    icon: `<svg fill="currentColor" viewBox="0 0 24 24"><path d="M12 3v10.55c-.59-.34-1.27-.55-2-.55-2.21 0-4 1.79-4 4s1.79 4 4 4 4-1.79 4-4V7h4V3h-6z"/></svg>`,
    bgColor: 'bg-gradient-to-r from-purple-500 to-pink-500'
  }
]

// Download CV function
const downloadCV = () => {
  // Create a temporary link element
  const link = document.createElement('a')
  link.href = 'src/assets/pdf/Un Mean Web Developer .pdf'
  link.download = 'Mean Un CV.pdf'
  document.body.appendChild(link)
  link.click()
  document.body.removeChild(link)
}

onMounted(() => {
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
  sr.reveal(headerSection.value, { delay: 200 })
  sr.reveal(aboutSection.value, { delay: 400 })
  sr.reveal(skillsSection.value, { delay: 600 })
  sr.reveal(projectsSection.value, { delay: 800 })
})
</script>

<style scoped>
/* Custom animations for skill tags */
.skill-tag {
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}

.skill-tag:hover {
  transform: translateY(-2px) scale(1.05);
}

/* Gradient animation */
@keyframes gradient {
  0%, 100% { background-position: 0% 50%; }
  50% { background-position: 100% 50%; }
}

.animate-gradient {
  background-size: 200% 200%;
  animation: gradient 3s ease infinite;
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