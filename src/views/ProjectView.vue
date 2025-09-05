<template>
  <section class="min-h-screen bg-gradient-to-br from-gray-50 to-blue-50 py-20 px-6">
    <div class="max-w-7xl mx-auto">
      <!-- Header -->
      <div class="text-center mb-16" ref="headerSection">
        <h1 class="text-4xl md:text-5xl font-bold text-gray-800 mb-4">
          My <span class="text-blue-600">Projects</span>
        </h1>
        <p class="text-gray-600 max-w-2xl mx-auto text-lg">
          A showcase of my journey as a Junior Web Developer, featuring projects from my studies at PNC and personal development.
        </p>
        <div class="w-24 h-1 bg-gradient-to-r from-blue-600 to-cyan-600 mx-auto rounded-full mt-6"></div>
      </div>

      <!-- Stats Section -->
      <div class="grid md:grid-cols-4 gap-6 mb-16" ref="statsSection">
        <div 
          v-for="stat in stats" 
          :key="stat.title"
          class="bg-white rounded-2xl shadow-lg p-6 text-center hover:shadow-xl transition-all duration-300 transform hover:-translate-y-2"
        >
          <div class="w-12 h-12 mx-auto mb-4 rounded-full flex items-center justify-center" :class="stat.bgColor">
            <div v-html="stat.icon" class="w-6 h-6 text-white"></div>
          </div>
          <div class="text-2xl font-bold mb-1" :class="stat.textColor">{{ stat.number }}</div>
          <p class="text-gray-600 text-sm">{{ stat.label }}</p>
        </div>
      </div>

      <!-- Filter Buttons -->
      <div class="flex flex-wrap justify-center gap-4 mb-12" ref="filterSection">
        <button
          v-for="category in categories"
          :key="category"
          @click="activeFilter = category"
          class="px-6 py-3 rounded-full font-medium transition-all duration-300 transform hover:scale-105"
          :class="activeFilter === category 
            ? 'bg-blue-600 text-white shadow-lg' 
            : 'bg-white text-gray-600 hover:bg-blue-50 shadow-md'"
        >
          {{ category }}
        </button>
      </div>

      <!-- Projects Grid -->
      <div class="space-y-12" ref="projectsSection">
        <div
          v-for="project in filteredProjects"
          :key="project.id"
          class="bg-white rounded-2xl shadow-lg overflow-hidden hover:shadow-xl transition-all duration-300"
        >
          <div class="grid lg:grid-cols-2 gap-0">
            <!-- Project Image/Visual -->
            <div class="relative h-64 lg:h-auto bg-gradient-to-br" :class="project.gradientBg">
              <div class="absolute inset-0 flex items-center justify-center">
                <div class="text-center text-white p-8">
                  <div v-html="project.icon" class="w-16 h-16 mx-auto mb-4 opacity-80"></div>
                  <h3 class="text-2xl font-bold mb-2">{{ project.title }}</h3>
                  <p class="text-sm opacity-90">{{ project.period }}</p>
                </div>
              </div>
              <!-- Project Status Badge -->
              <div class="absolute top-4 right-4">
                <span class="px-3 py-1 text-xs font-medium rounded-full" :class="getStatusColor(project.status)">
                  {{ project.status }}
                </span>
              </div>
            </div>

            <!-- Project Content -->
            <div class="p-8">
              <div class="flex items-center justify-between mb-4">
                <span class="px-3 py-1 text-xs font-medium rounded-full" :class="getCategoryColor(project.category)">
                  {{ project.category }}
                </span>
                <span class="text-sm text-gray-500">{{ project.teamSize }}</span>
              </div>
              
              <h3 class="text-2xl font-bold text-gray-800 mb-4">{{ project.title }}</h3>
              
              <p class="text-gray-600 mb-6 leading-relaxed">
                {{ project.description }}
              </p>

              <!-- Key Features -->
              <div class="mb-6" v-if="project.features">
                <h4 class="font-semibold text-gray-800 mb-3">Key Features:</h4>
                <ul class="space-y-2">
                  <li v-for="feature in project.features" :key="feature" class="flex items-start">
                    <svg class="w-4 h-4 text-green-500 mt-1 mr-2 flex-shrink-0" fill="currentColor" viewBox="0 0 20 20">
                      <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd" />
                    </svg>
                    <span class="text-gray-600 text-sm">{{ feature }}</span>
                  </li>
                </ul>
              </div>

              <!-- Technologies -->
              <div class="mb-6">
                <h4 class="font-semibold text-gray-800 mb-3">Technologies Used:</h4>
                <div class="flex flex-wrap gap-2">
                  <span 
                    v-for="tech in project.technologies" 
                    :key="tech"
                    class="px-3 py-1 text-xs bg-gray-100 text-gray-700 rounded-full hover:bg-blue-100 hover:text-blue-700 transition-colors duration-200"
                  >
                    {{ tech }}
                  </span>
                </div>
              </div>

              <!-- My Role -->
              <div class="mb-6" v-if="project.role">
                <h4 class="font-semibold text-gray-800 mb-2">My Role:</h4>
                <p class="text-gray-600 text-sm">{{ project.role }}</p>
              </div>

              <!-- Project Links -->
              <div class="flex flex-wrap gap-3">
                <a 
                  v-if="project.liveUrl" 
                  :href="project.liveUrl" 
                  target="_blank" 
                  rel="noopener noreferrer"
                  class="flex items-center px-4 py-2 bg-blue-600 text-white rounded-lg hover:bg-blue-700 transition-colors duration-300 text-sm font-medium"
                >
                  <svg class="w-4 h-4 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 6H6a2 2 0 00-2 2v10a2 2 0 002 2h10a2 2 0 002-2v-4M14 4h6m0 0v6m0-6L10 14" />
                  </svg>
                  View Live
                </a>
                <a 
                  v-if="project.githubUrl" 
                  :href="project.githubUrl" 
                  target="_blank" 
                  rel="noopener noreferrer"
                  class="flex items-center px-4 py-2 border border-gray-300 text-gray-700 rounded-lg hover:bg-gray-50 transition-colors duration-300 text-sm font-medium"
                >
                  <svg class="w-4 h-4 mr-2" fill="currentColor" viewBox="0 0 24 24">
                    <path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/>
                  </svg>
                  View Code
                </a>
                <button 
                  v-if="project.hasDemo"
                  @click="openDemo(project)"
                  class="flex items-center px-4 py-2 bg-green-600 text-white rounded-lg hover:bg-green-700 transition-colors duration-300 text-sm font-medium"
                >
                  <svg class="w-4 h-4 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M14.828 14.828a4 4 0 01-5.656 0M9 10h1m4 0h1m-6 4h.01M15 14h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
                  </svg>
                  View Demo
                </button>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- Skills Gained Section -->
      <div class="mt-20 bg-white rounded-2xl shadow-lg p-12" ref="skillsSection">
        <div class="text-center mb-12">
          <h2 class="text-3xl font-bold text-gray-800 mb-4">Skills Gained Through Projects</h2>
          <p class="text-gray-600 max-w-2xl mx-auto">
            Each project has contributed to my growth as a developer, helping me master various technologies and methodologies.
          </p>
        </div>

        <div class="grid md:grid-cols-3 gap-8">
          <div 
            v-for="skillCategory in skillCategories" 
            :key="skillCategory.title"
            class="text-center"
          >
            <div class="w-16 h-16 mx-auto mb-6 rounded-full flex items-center justify-center" :class="skillCategory.bgColor">
              <div v-html="skillCategory.icon" class="w-8 h-8 text-white"></div>
            </div>
            <h3 class="text-xl font-bold text-gray-800 mb-4">{{ skillCategory.title }}</h3>
            <div class="flex flex-wrap justify-center gap-2">
              <span 
                v-for="skill in skillCategory.skills" 
                :key="skill"
                class="px-3 py-1 text-sm bg-gray-100 text-gray-700 rounded-full hover:bg-blue-100 hover:text-blue-700 transition-colors duration-200"
              >
                {{ skill }}
              </span>
            </div>
          </div>
        </div>
      </div>

      <!-- Contact CTA -->
      <div class="mt-20 text-center bg-gradient-to-r from-blue-600 to-cyan-600 rounded-2xl shadow-lg p-12 text-white" ref="ctaSection">
        <h2 class="text-3xl font-bold mb-4">
          Interested in Working Together?
        </h2>
        <p class="mb-8 max-w-2xl mx-auto opacity-90">
          I'm always excited to take on new challenges and collaborate on interesting projects. 
          Let's discuss how we can bring your ideas to life!
        </p>
        <div class="flex flex-col sm:flex-row gap-4 justify-center">
          <RouterLink
            to="/contact"
            class="inline-block bg-white text-blue-600 font-semibold py-4 px-8 rounded-full shadow-lg hover:shadow-xl transform hover:-translate-y-1 transition-all duration-300"
          >
            Get In Touch
          </RouterLink>
          <a
            href="mailto:mean.un@student.passerellesnumeriques.org"
            class="inline-block border-2 border-white text-white font-semibold py-4 px-8 rounded-full hover:bg-white hover:text-blue-600 transition-all duration-300"
          >
            Send Email
          </a>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, computed, onMounted } from 'vue'
import { RouterLink } from 'vue-router'
import ScrollReveal from 'scrollreveal'

// Template refs
const headerSection = ref(null)
const statsSection = ref(null)
const filterSection = ref(null)
const projectsSection = ref(null)
const skillsSection = ref(null)
const ctaSection = ref(null)

// Reactive data
const activeFilter = ref('All')

// Stats data
const stats = [
  {
    title: 'Projects',
    number: '9+',
    label: 'Completed Projects',
    icon: `<svg fill="currentColor" viewBox="0 0 24 24"><path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zm-5 14H7v-2h7v2zm3-4H7v-2h10v2zm0-4H7V7h10v2z"/></svg>`,
    bgColor: 'bg-gradient-to-r from-blue-500 to-cyan-500',
    textColor: 'text-blue-600'
  },
  {
    title: 'Technologies',
    number: '15+',
    label: 'Technologies Mastered',
    icon: `<svg fill="currentColor" viewBox="0 0 24 24"><path d="M9.4 16.6L4.8 12l4.6-4.6L8 6l-6 6 6 6 1.4-1.4zm5.2 0L19.2 12l-4.6-4.6L16 6l6 6-6 6-1.4-1.4z"/></svg>`,
    bgColor: 'bg-gradient-to-r from-green-500 to-emerald-500',
    textColor: 'text-green-600'
  },
  {
    title: 'Team Projects',
    number: '9+',
    label: 'Collaborative Works',
    icon: `<svg fill="currentColor" viewBox="0 0 24 24"><path d="M16 7a4 4 0 11-8 0 4 4 0 018 0zM12 14a7 7 0 00-7 7h14a7 7 0 00-7-7z"/></svg>`,
    bgColor: 'bg-gradient-to-r from-purple-500 to-pink-500',
    textColor: 'text-purple-600'
  },
  {
    title: 'Experience',
    number: '1.5+',
    label: 'Years Learning',
    icon: `<svg fill="currentColor" viewBox="0 0 24 24"><path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm-2 15l-5-5 1.41-1.41L10 14.17l7.59-7.59L19 8l-9 9z"/></svg>`,
    bgColor: 'bg-gradient-to-r from-orange-500 to-red-500',
    textColor: 'text-orange-600'
  }
]

// Categories
const categories = ['All', 'Full Stack', 'Frontend', 'Backend', 'Mobile', 'Design']

// Projects data based on your CV
const projects = [
  {
    id: 0,
    title: 'Booking Travel App',
    description: 'Seft learning to create a app system for booking room in hotel with adventure place that user want to go and travel with their family or friends.',
    period: 'June 21 - August 29, 2025',
    category: 'Mobile',
    teamSize: 'Team of 5',
    role: 'Mobile Developer, Backend & Frontend Developer',
    status: 'Completed',
    technologies: ['Flutter', 'Dart', 'Laravel', 'MySQL', 'Jira', 'Git'],
    features: [
      'Booking room and view Hotel and Adventure Place',
      'User authentication and authorization system',
      
    ],
    gradientBg: 'from-pink-500 to-rose-500',
    icon: `<svg fill="currentColor" viewBox="0 0 24 24"><path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm-2 15l-5-5 1.41-1.41L10 14.17l7.59-7.59L19 8l-9 9z"/></svg>`,
    // liveUrl: 'https://your-beauty-store.com',
    githubUrl: 'https://github.com/kimchhik-chhuong/booking_room_travel',
  },
  {
    id: 1,
    title: 'Beauty Store System',
    description: 'A system for a beauty store that allows users to manage their products, send promotions, track orders and user history.',
    period: 'Mar 10 - Apr 2, 2025',
    category: 'Full Stack',
    teamSize: 'Team of 6',
    role: 'DevOps, Backend & Frontend Developer',
    status: 'Completed',
    technologies: ['HTML', 'CSS', 'JavaScript', 'Bootstrap', 'PHP', 'MySQL', 'AWS EC2', 'Telegram Bot', 'Git', 'Jira', 'Figma'],
    features: [
      'User authentication and authorization system',
      'Product catalog with search and filtering',
      'Shopping cart and checkout process',
      'Admin panel for product and user management',
      'Telegram bot integration for promotions',
      'Order history and tracking',
      'Responsive design for all devices'
    ],
    gradientBg: 'from-pink-500 to-rose-500',
    icon: `<svg fill="currentColor" viewBox="0 0 24 24"><path d="M7 18c-1.1 0-2 .9-2 2s.9 2 2 2 2-.9 2-2-.9-2-2-2zM1 2v2h2l3.6 7.59-1.35 2.45c-.16.28-.25.61-.25.96 0 1.1.9 2 2 2h12v-2H7.42c-.14 0-.25-.11-.25-.25l.03-.12L8.1 13h7.45c.75 0 1.41-.41 1.75-1.03L21.7 4H5.21l-.94-2H1zm16 16c-1.1 0-2 .9-2 2s.9 2 2 2 2-.9 2-2-.9-2-2-2z"/></svg>`,
    // liveUrl: 'https://your-beauty-store.com',
    githubUrl: 'https://github.com/liikaa7zip/beauty_store_G13',
  },
  {
    id: 2,
    title: 'Expense Management Website',
    description: 'A responsive web application designed to help users track and manage their personal expenses. Features include adding, editing, and deleting expense records with categorization and visual reporting through charts and graphs.',
    period: 'Jan 14 - 29, 2025',
    category: 'Frontend',
    teamSize: 'Team of 3',
    role: 'Full Stack Developer',
    status: 'Completed',
    technologies: ['HTML', 'CSS', 'JavaScript', 'Chart.js', 'Local Storage', 'Firebase'],
    features: [
      'Add, edit, and delete expense entries',
      'Expense categorization system',
      'Visual charts and graphs for spending analysis',
      'Monthly and yearly expense summaries',
      'Data persistence using local storage',
      'Responsive design for mobile and desktop',
      'Export data functionality',
      'Authentication and authorization system with friebase',
    ],
    gradientBg: 'from-green-500 to-emerald-500',
    icon: `<svg fill="currentColor" viewBox="0 0 24 24"><path d="M11.8 10.9c-2.27-.59-3-1.2-3-2.15 0-1.09 1.01-1.85 2.7-1.85 1.78 0 2.44.85 2.5 2.1h2.21c-.07-1.72-1.12-3.3-3.21-3.81V3h-3v2.16c-1.94.42-3.5 1.68-3.5 3.61 0 2.31 1.91 3.46 4.7 4.13 2.5.6 3 1.48 3 2.41 0 .69-.49 1.79-2.7 1.79-2.06 0-2.87-.92-2.98-2.1h-2.2c.12 2.19 1.76 3.42 3.68 3.83V21h3v-2.15c1.95-.37 3.5-1.5 3.5-3.55 0-2.84-2.43-3.81-4.7-4.4z"/></svg>`,
    // liveUrl: 'https://meanun-expense-tracker.netlify.app',
    githubUrl: 'https://github.com/Mean-UN/Project-JavaScript-G14',
    // hasDemo: true
  },
  {
    id: 3,
    title: 'WordPress Deployment on AWS',
    description: 'Successfully deployed and configured a WordPress website on Amazon Web Services EC2 instance. This project involved server setup, database configuration, security implementation, and performance optimization.',
    period: 'Dec 31, 2024 - Jan 5, 2025',
    category: 'Backend',
    teamSize: 'Individual Project',
    role: 'DevOps Engineer',
    status: 'Completed',
    technologies: ['WordPress', 'AWS EC2', 'Linux Ubuntu', 'MySQL', 'Apache', 'SSL'],
    features: [
      'EC2 instance setup and configuration',
      'WordPress installation and customization',
      'MySQL database setup and optimization',
      'Organization of the project',
    ],
    gradientBg: 'from-blue-500 to-indigo-500',
    icon: `<svg fill="currentColor" viewBox="0 0 24 24"><path d="M21.469 6.825c.84 1.537 1.318 3.3 1.318 5.175 0 3.979-2.156 7.456-5.363 9.325l3.295-9.527c.615-1.54.82-2.771.82-3.864 0-.405-.026-.78-.07-1.11m-7.981.105c.647-.03 1.232-.105 1.232-.105.582-.075.514-.93-.067-.899 0 0-1.755.135-2.88.135-1.064 0-2.85-.135-2.85-.135-.584-.031-.661.854-.082.899 0 0 .537.075 1.104.105l1.644 4.505L9.281 18.675l-2.926-8.78c.647-.03 1.232-.105 1.232-.105.582-.075.515-.93-.067-.899 0 0-1.755.135-2.88.135-.203 0-.44-.016-.69-.023C4.719 6.993 6.73 6.025 8.97 6.025c1.36 0 2.598.528 3.515 1.389-.022-.001-.04-.009-.062-.009-.203 0-.375.018-.375.018-.584.031-.661.854-.082.899 0 0 .537.075 1.104.105l1.644 4.505L9.281 18.675l-2.926-8.78z"/></svg>`,
    // liveUrl: 'https://your-wordpress-site.com',
    githubUrl: null,
    // hasDemo: false
  },
  {
    id: 4,
    title: 'Sports Clue Website',
    description: 'A mini website themed around sports clue gathering, developed as part of a web design project. The site features interactive elements, responsive design, and engaging user interface for sports enthusiasts.',
    period: 'Oct 21 - Nov 5, 2024',
    category: 'Frontend',
    teamSize: 'Team of 3',
    role: 'Frontend Developer',
    status: 'Completed',
    technologies: ['HTML', 'CSS', 'SASS', 'JavaScript', 'Responsive Design'],
    features: [
      'Interactive sports clue games',
      'Responsive design for all devices',
      'Modern CSS animations and transitions',
      'User-friendly navigation system',
      'Sports-themed visual design',
      'Cross-browser compatibility'
    ],
    gradientBg: 'from-orange-500 to-yellow-500',
    icon: `<svg fill="currentColor" viewBox="0 0 24 24"><path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm-2 15l-5-5 1.41-1.41L10 14.17l7.59-7.59L19 8l-9 9z"/></svg>`,
    // liveUrl: 'https://sports-clue-website.netlify.app',
    githubUrl: 'https://github.com/samounsuon/Sport-Club',
    // hasDemo: true
  },
  {
    id: 5,
    title: 'Music Voice Controller',
    description: 'An innovative Python application that allows users to control music playback using voice commands. Built with Tkinter for the GUI and integrated voice recognition for hands-free music control.',
    period: 'Nov 18 - 28, 2024',
    category: 'Mobile',
    teamSize: 'Team of 3',
    role: 'Python Developer',
    status: 'Completed',
    technologies: ['Python', 'Tkinter', 'Speech Recognition', 'Audio Processing'],
    features: [
      'Voice command recognition',
      'Music playback control (play, pause, next, previous)',
      'Volume control via voice',
      'Playlist management',
      'User-friendly GUI interface',
      'Real-time voice feedback'
    ],
    gradientBg: 'from-purple-500 to-pink-500',
    icon: `<svg fill="currentColor" viewBox="0 0 24 24"><path d="M12 3v10.55c-.59-.34-1.27-.55-2-.55-2.21 0-4 1.79-4 4s1.79 4 4 4 4-1.79 4-4V7h4V3h-6z"/></svg>`,
    liveUrl: null,
    githubUrl: 'https://github.com/Mean74student/Project-Voice-Control-Music-by-Python-M-K-L',
    hasDemo: false
  },
  {
    id: 6,
    title: 'Culinary Club Brochure Design',
    description: 'Designed a comprehensive brochure and app wireframes for a culinary club using Figma. The project focused on creating visually appealing designs that effectively communicate the club\'s activities and attract new members.',
    period: 'Jun 18 - Aug 28, 2024',
    category: 'Design',
    teamSize: 'Team of 4',
    role: 'UI/UX Designer',
    status: 'Completed',
    technologies: ['Figma', 'Adobe Illustrator', 'Design Thinking', 'Wireframing'],
    features: [
      'Professional brochure design',
      'Mobile app wireframes',
      'Brand identity development',
      'User experience optimization',
      'Print-ready design files',
      'Interactive prototypes'
    ],
    gradientBg: 'from-red-500 to-pink-500',
    icon: `<svg fill="currentColor" viewBox="0 0 24 24"><path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/></svg>`,
    // liveUrl: 'https://figma.com/your-design-link',
    // githubUrl: null,
    // hasDemo: true
  }
]

// Skills gained through projects
const skillCategories = [
  {
    title: 'Frontend Development',
    skills: ['HTML/CSS', 'JavaScript', 'Vue.js', 'Bootstrap', 'Tailwind CSS', 'SASS', 'Responsive Design', ],
    icon: `<svg fill="currentColor" viewBox="0 0 24 24"><path d="M9.75 17L9 20l-1 1h8l-1-1-.75-3M3 13h18M5 17h14a2 2 0 002-2V5a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"/></svg>`,
    bgColor: 'bg-gradient-to-r from-blue-500 to-cyan-500'
  },
  {
    title: 'Backend & Database',
    skills: ['PHP', 'Laravel', 'MySQL', 'Node.js', 'REST API', 'AWS EC2'],
    icon: `<svg fill="currentColor" viewBox="0 0 24 24"><path d="M5 12h14M5 12a2 2 0 01-2-2V6a2 2 0 012-2h14a2 2 0 012 2v4a2 2 0 01-2 2M5 12a2 2 0 00-2 2v4a2 2 0 002 2h14a2 2 0 002-2v-4a2 2 0 00-2-2m-2-4h.01M17 16h.01"/></svg>`,
    bgColor: 'bg-gradient-to-r from-green-500 to-emerald-500'
  },
  {
    title: 'Tools & DevOps',
    skills: ['Git/GitHub', 'AWS', 'Linux', 'Figma', 'Jira', 'WordPress' , 'AI tools', 'MS Office',],
    icon: `<svg fill="currentColor" viewBox="0 0 24 24"><path d="M22.46 6c-.77.35-1.6.58-2.46.69.88-.53 1.56-1.37 1.88-2.38-.83.5-1.75.85-2.72 1.05C18.37 4.5 17.26 4 16 4c-2.35 0-4.27 1.92-4.27 4.29 0 .34.04.67.11.98C8.28 9.09 5.11 7.38 3 4.79c-.37.63-.58 1.37-.58 2.15 0 1.49.75 2.81 1.91 3.56-.71 0-1.37-.2-1.95-.5v.03c0 2.08 1.48 3.82 3.44 4.21a4.22 4.22 0 0 1-1.93.07 4.28 4.28 0 0 0 4 2.98 8.521 8.521 0 0 1-5.33 1.84c-.34 0-.68-.02-1.02-.06C3.44 20.29 5.7 21 8.12 21 16 21 20.33 14.46 20.33 8.79c0-.19 0-.37-.01-.56.84-.6 1.56-1.36 2.14-2.23z"/></svg>`,
    bgColor: 'bg-gradient-to-r from-purple-500 to-pink-500'
  }
]

// Computed properties
const filteredProjects = computed(() => {
  if (activeFilter.value === 'All') {
    return projects
  }
  return projects.filter(project => project.category === activeFilter.value)
})

// Methods
const getCategoryColor = (category) => {
  const colors = {
    'Full Stack': 'bg-blue-100 text-blue-800',
    'Frontend': 'bg-green-100 text-green-800',
    'Backend': 'bg-purple-100 text-purple-800',
    'Mobile': 'bg-orange-100 text-orange-800',
    'Design': 'bg-pink-100 text-pink-800'
  }
  return colors[category] || 'bg-gray-100 text-gray-800'
}

const getStatusColor = (status) => {
  const colors = {
    'Completed': 'bg-green-100 text-green-800',
    'In Progress': 'bg-yellow-100 text-yellow-800',
    'Planning': 'bg-blue-100 text-blue-800'
  }
  return colors[status] || 'bg-gray-100 text-gray-800'
}

const openDemo = (project) => {
  // You can implement a modal or redirect to demo
  if (project.liveUrl) {
    window.open(project.liveUrl, '_blank')
  }
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
  sr.reveal(statsSection.value, { delay: 400 })
  sr.reveal(filterSection.value, { delay: 600 })
  sr.reveal(projectsSection.value, { delay: 800 })
  sr.reveal(skillsSection.value, { delay: 1000 })
  sr.reveal(ctaSection.value, { delay: 1200 })
})
</script>

<style scoped>
/* Custom animations */
@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.animate-fadeInUp {
  animation: fadeInUp 0.6s ease-out;
}

/* Hover effects */
.group:hover .group-hover\:scale-110 {
  transform: scale(1.1);
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

/* Responsive adjustments */
@media (max-width: 768px) {
  .grid.lg\\:grid-cols-2 {
    grid-template-columns: 1fr;
  }
}
</style>