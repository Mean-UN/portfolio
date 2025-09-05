<template>
  <div id="app" class="min-h-screen bg-gray-50">
    <!-- Skip to main content for accessibility -->
    <a href="#main-content" class="sr-only focus:not-sr-only focus:absolute focus:top-4 focus:left-4 bg-blue-600 text-white px-4 py-2 rounded-md z-50">
      Skip to main content
    </a>

    <!-- Navigation Header -->
    <header class="relative">
      <nav 
        class="fixed w-full bg-white/95 backdrop-blur-md z-50 transition-all duration-300 border-b border-gray-100/50"
        :class="[
          isScrolled ? 'h-14 sm:h-16 shadow-lg' : 'h-16 sm:h-20 shadow-sm',
        ]"
        role="navigation"
        aria-label="Main navigation"
      >
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 h-full">
          <div class="flex items-center justify-between h-full">
            <!-- Logo -->
            <RouterLink 
              to="/" 
              class="relative group flex items-center" 
              @click="closeMenu"
              aria-label="Mean Un - Home"
            >
              <div class="flex items-center">
                <span class="text-xl sm:text-2xl font-bold text-cyan-600 group-hover:text-cyan-700 transition-colors duration-200">
                  Mean
                </span>
                <span class="text-2xl sm:text-4xl text-gray-400 group-hover:text-gray-600 transition-colors duration-200 ml-1">
                  .
                </span>
              </div>
              <!-- Logo hover effect -->
              <div class="absolute -bottom-1 left-0 w-0 h-0.5 bg-cyan-600 transition-all duration-300 group-hover:w-full"></div>
            </RouterLink>

            <!-- Desktop Navigation -->
            <div class="hidden md:flex items-center space-x-4 lg:space-x-8">
              <nav class="flex space-x-4 lg:space-x-6" role="menubar">
                <RouterLink 
                  v-for="link in navigationLinks"
                  :key="link.to"
                  :to="link.to"
                  class="relative font-medium text-gray-700 hover:text-cyan-600 transition-all duration-200 py-2 px-3 rounded-md hover:bg-cyan-50 text-sm lg:text-base group"
                  active-class="text-cyan-600 bg-cyan-50"
                  role="menuitem"
                  :aria-current="route.path === link.to ? 'page' : undefined"
                >
                  <span class="flex items-center">
                    <component :is="link.icon" class="w-4 h-4 mr-2 opacity-70 group-hover:opacity-100 transition-opacity" />
                    {{ link.label }}
                  </span>
                  <!-- Active indicator -->
                  <span 
                    class="absolute bottom-0 left-1/2 transform -translate-x-1/2 w-0 h-0.5 bg-cyan-600 transition-all duration-200"
                    :class="route.path === link.to ? 'w-8' : 'group-hover:w-6'"
                  ></span>
                </RouterLink>
              </nav>
              
              <!-- Download CV Button -->
              <button 
                @click="downloadCV"
                class="group relative px-4 lg:px-6 py-2 lg:py-2.5 rounded-lg bg-gradient-to-r from-gray-100 to-gray-200 hover:from-cyan-500 hover:to-cyan-600 text-gray-700 hover:text-white transition-all duration-300 font-medium shadow-sm hover:shadow-md transform hover:-translate-y-0.5 text-sm lg:text-base focus:outline-none focus:ring-2 focus:ring-cyan-500 focus:ring-offset-2"
                :disabled="isDownloading"
                :aria-label="isDownloading ? 'Downloading CV...' : 'Download CV'"
              >
                <span class="flex items-center">
                  <span class="hidden sm:inline">{{ isDownloading ? 'Downloading...' : 'Download CV' }}</span>
                  <span class="sm:hidden">{{ isDownloading ? '...' : 'CV' }}</span>
                  <svg 
                    v-if="!isDownloading"
                    class="w-3 h-3 lg:w-4 lg:h-4 ml-1 lg:ml-2 transition-transform group-hover:translate-y-1" 
                    fill="none" 
                    stroke="currentColor" 
                    viewBox="0 0 24 24"
                  >
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 10v6m0 0l-3-3m3 3l3-3m2 8H7a2 2 0 01-2-2V5a2 2 0 012-2h5.586a1 1 0 01.707.293l5.414 5.414a1 1 0 01.293.707V19a2 2 0 01-2 2z" />
                  </svg>
                  <svg 
                    v-else
                    class="w-3 h-3 lg:w-4 lg:h-4 ml-1 lg:ml-2 animate-spin" 
                    fill="none" 
                    stroke="currentColor" 
                    viewBox="0 0 24 24"
                  >
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 4v5h.582m15.356 2A8.001 8.001 0 004.582 9m0 0H9m11 11v-5h-.581m0 0a8.003 8.003 0 01-15.357-2m15.357 2H15" />
                  </svg>
                </span>
              </button>
            </div>

            <!-- Mobile Menu Button -->
            <button 
              id="menu-button"
              @click="toggleMenu"
              class="md:hidden p-2 rounded-lg hover:bg-gray-100 transition-colors duration-200 focus:outline-none focus:ring-2 focus:ring-cyan-500 focus:ring-offset-2"
              :class="{ 'bg-gray-100': isMenuOpen }"
              :aria-expanded="isMenuOpen"
              aria-controls="mobile-menu"
              aria-label="Toggle navigation menu"
            >
              <div class="w-6 h-6 flex flex-col justify-center items-center">
                <span 
                  class="block w-5 h-0.5 bg-gray-600 transition-all duration-300"
                  :class="isMenuOpen ? 'rotate-45 translate-y-1' : '-translate-y-1'"
                ></span>
                <span 
                  class="block w-5 h-0.5 bg-gray-600 transition-all duration-300"
                  :class="isMenuOpen ? 'opacity-0' : 'opacity-100'"
                ></span>
                <span 
                  class="block w-5 h-0.5 bg-gray-600 transition-all duration-300"
                  :class="isMenuOpen ? '-rotate-45 -translate-y-1' : 'translate-y-1'"
                ></span>
              </div>
            </button>
          </div>

          <!-- Mobile Menu -->
          <div 
            id="mobile-menu"
            class="md:hidden absolute top-full left-0 w-full bg-white/95 backdrop-blur-md shadow-lg transition-all duration-300 overflow-hidden border-b border-gray-100/50"
            :class="isMenuOpen ? 'max-h-96 opacity-100' : 'max-h-0 opacity-0'"
            :aria-hidden="!isMenuOpen"
            role="menu"
          >
            <nav class="px-4 py-4 space-y-2">
              <RouterLink 
                v-for="link in navigationLinks"
                :key="link.to"
                :to="link.to"
                @click="closeMenu"
                class="flex items-center px-4 py-3 rounded-lg font-medium text-gray-700 hover:text-cyan-600 hover:bg-gray-50 transition-all duration-200 group"
                active-class="text-cyan-600 bg-cyan-50"
                role="menuitem"
                :aria-current="route.path === link.to ? 'page' : undefined"
              >
                <component :is="link.icon" class="w-5 h-5 mr-3 opacity-70 group-hover:opacity-100 transition-opacity" />
                {{ link.label }}
              </RouterLink>
              
              <!-- Mobile Download CV Button -->
              <button 
                @click="downloadCV(); closeMenu()"
                class="w-full mt-4 px-4 py-3 rounded-lg bg-gradient-to-r from-cyan-500 to-cyan-600 text-white font-medium shadow-md hover:shadow-lg transition-all duration-300 flex items-center justify-center focus:outline-none focus:ring-2 focus:ring-cyan-500 focus:ring-offset-2"
                :disabled="isDownloading"
              >
                <svg class="w-4 h-4 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 10v6m0 0l-3-3m3 3l3-3m2 8H7a2 2 0 01-2-2V5a2 2 0 012-2h5.586a1 1 0 01.707.293l5.414 5.414a1 1 0 01.293.707V19a2 2 0 01-2 2z" />
                </svg>
                {{ isDownloading ? 'Downloading...' : 'Download CV' }}
              </button>
            </nav>
          </div>
        </div>
      </nav>

      <!-- Progress Bar -->
      <div 
        class="fixed top-0 left-0 h-1 bg-gradient-to-r from-cyan-500 to-blue-500 z-50 transition-all duration-300"
        :style="{ width: scrollProgress + '%' }"
      ></div>
    </header>

    <!-- Main Content -->
    <main 
      id="main-content"
      class="pt-16 sm:pt-20 min-h-screen"
      role="main"
    >
      <RouterView v-slot="{ Component, route }">
        <Transition 
          :name="getTransitionName(route)"
          mode="out-in"
          @enter="onPageEnter"
          @leave="onPageLeave"
        >
          <component :is="Component" :key="route.path" />
        </Transition>
      </RouterView>
    </main>

    <!-- Back to Top Button -->
    <Transition name="fade">
      <button
        v-if="showBackToTop"
        @click="scrollToTop"
        class="fixed bottom-6 right-6 w-12 h-12 bg-cyan-600 hover:bg-cyan-700 text-white rounded-full shadow-lg hover:shadow-xl transition-all duration-300 transform hover:scale-110 focus:outline-none focus:ring-2 focus:ring-cyan-500 focus:ring-offset-2 z-40"
        aria-label="Back to top"
      >
        <svg class="w-6 h-6 mx-auto" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 10l7-7m0 0l7 7m-7-7v18" />
        </svg>
      </button>
    </Transition>

    <!-- Loading Overlay -->
    <Transition name="fade">
      <div 
        v-if="isLoading"
        class="fixed inset-0 bg-white/80 backdrop-blur-sm z-50 flex items-center justify-center"
      >
        <div class="text-center">
          <div class="w-12 h-12 border-4 border-cyan-200 border-t-cyan-600 rounded-full animate-spin mx-auto mb-4"></div>
          <p class="text-gray-600 font-medium">Loading...</p>
        </div>
      </div>
    </Transition>

    <!-- Toast Notifications -->
    <Transition name="slide-up">
      <div 
        v-if="toast.show"
        class="fixed bottom-6 left-6 right-6 sm:left-auto sm:right-6 sm:w-96 bg-white border border-gray-200 rounded-lg shadow-lg p-4 z-50"
        :class="{
          'border-green-200 bg-green-50': toast.type === 'success',
          'border-red-200 bg-red-50': toast.type === 'error',
          'border-blue-200 bg-blue-50': toast.type === 'info'
        }"
      >
        <div class="flex items-center">
          <div 
            class="flex-shrink-0 w-5 h-5 mr-3"
            :class="{
              'text-green-600': toast.type === 'success',
              'text-red-600': toast.type === 'error',
              'text-blue-600': toast.type === 'info'
            }"
          >
            <svg v-if="toast.type === 'success'" fill="currentColor" viewBox="0 0 20 20">
              <path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z" clip-rule="evenodd" />
            </svg>
            <svg v-else-if="toast.type === 'error'" fill="currentColor" viewBox="0 0 20 20">
              <path fill-rule="evenodd" d="M18 10a8 8 0 11-16 0 8 8 0 0116 0zm-7 4a1 1 0 11-2 0 1 1 0 012 0zm-1-9a1 1 0 00-1 1v4a1 1 0 102 0V6a1 1 0 00-1-1z" clip-rule="evenodd" />
            </svg>
            <svg v-else fill="currentColor" viewBox="0 0 20 20">
              <path fill-rule="evenodd" d="M18 10a8 8 0 11-16 0 8 8 0 0116 0zm-7-4a1 1 0 000 2v3a1 1 0 101 1h1a1 1 0 100-2v-3a1 1 0 00-1-1H9z" clip-rule="evenodd" />
            </svg>
          </div>
          <p class="text-sm font-medium text-gray-900">{{ toast.message }}</p>
          <button 
            @click="hideToast"
            class="ml-auto flex-shrink-0 text-gray-400 hover:text-gray-600 transition-colors"
          >
            <svg class="w-4 h-4" fill="currentColor" viewBox="0 0 20 20">
              <path fill-rule="evenodd" d="M4.293 4.293a1 1 0 011.414 0L10 8.586l4.293-4.293a1 1 0 111.414 1.414L11.414 10l4.293 4.293a1 1 0 01-1.414 1.414L10 11.414l-4.293 4.293a1 1 0 01-1.414-1.414L8.586 10 4.293 5.707a1 1 0 010-1.414z" clip-rule="evenodd" />
            </svg>
          </button>
        </div>
      </div>
    </Transition>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted, reactive, computed, nextTick } from 'vue'
import { RouterLink, RouterView, useRoute, useRouter } from 'vue-router'
const cvPdf = '/Un-Mean-Web-Developer-CV.pdf'

// Router
const route = useRoute()
const router = useRouter()

// Reactive state
const isMenuOpen = ref(false)
const isScrolled = ref(false)
const isDownloading = ref(false)
const isLoading = ref(false)
const scrollProgress = ref(0)
const showBackToTop = ref(false)

// Toast notification system
const toast = reactive({
  show: false,
  message: '',
  type: 'info' // 'success', 'error', 'info'
})

// Navigation links with icons
const navigationLinks = [
  { 
    to: '/', 
    label: 'Home',
    icon: 'svg' // We'll use inline SVG
  },
  { 
    to: '/about', 
    label: 'About',
    icon: 'svg'
  },
  { 
    to: '/projects', 
    label: 'Projects',
    icon: 'svg'
  },
  { 
    to: '/contact', 
    label: 'Contact',
    icon: 'svg'
  }
]

// Computed properties
const currentPageTitle = computed(() => {
  const titles = {
    '/': 'Home',
    '/about': 'About',
    '/projects': 'Projects',
    '/contact': 'Contact'
  }
  return titles[route.path] || 'Portfolio'
})

// Methods
const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value
  // Prevent body scroll when menu is open
  document.body.style.overflow = isMenuOpen.value ? 'hidden' : ''
}

const closeMenu = () => {
  isMenuOpen.value = false
  document.body.style.overflow = ''
}

const handleScroll = () => {
  const scrollTop = window.pageYOffset || document.documentElement.scrollTop
  const scrollHeight = document.documentElement.scrollHeight - window.innerHeight
  
  isScrolled.value = scrollTop > 50
  scrollProgress.value = (scrollTop / scrollHeight) * 100
  showBackToTop.value = scrollTop > 300
}

const handleResize = () => {
  if (window.innerWidth >= 768) {
    closeMenu()
  }
}

const handleClickOutside = (e) => {
  if (!e.target.closest('#mobile-menu') && !e.target.closest('#menu-button')) {
    closeMenu()
  }
}

const downloadCV = async () => {
  if (isDownloading.value) return

  isDownloading.value = true

  try {
    // Simulate download delay for better UX
    await new Promise(resolve => setTimeout(resolve, 1000))

    const link = document.createElement('a')
    link.href = cvPdf
    link.download = 'Mean Un CV.pdf'
    document.body.appendChild(link)
    link.click()
    document.body.removeChild(link)

    showToast('CV downloaded successfully!', 'success')
  } catch (error) {
    console.error('Download failed:', error)
    showToast('Failed to download CV. Please try again.', 'error')
  } finally {
    isDownloading.value = false
  }
}

const scrollToTop = () => {
  window.scrollTo({
    top: 0,
    behavior: 'smooth'
  })
}

const showToast = (message, type = 'info') => {
  toast.message = message
  toast.type = type
  toast.show = true
  
  // Auto hide after 3 seconds
  setTimeout(() => {
    hideToast()
  }, 3000)
}

const hideToast = () => {
  toast.show = false
}

const getTransitionName = (route) => {
  // You can customize transitions based on route
  return 'page'
}

const onPageEnter = () => {
  isLoading.value = false
}

const onPageLeave = () => {
  isLoading.value = true
}

// Lifecycle hooks
onMounted(() => {
  window.addEventListener('scroll', handleScroll, { passive: true })
  window.addEventListener('resize', handleResize)
  document.addEventListener('click', handleClickOutside)
  
  // Set initial scroll state
  handleScroll()
  
  // Update document title
  document.title = `${currentPageTitle.value} - Mean Un Portfolio`
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
  window.removeEventListener('resize', handleResize)
  document.removeEventListener('click', handleClickOutside)
  document.body.style.overflow = ''
})

// Watch route changes
router.afterEach((to) => {
  closeMenu()
  document.title = `${currentPageTitle.value} - Mean Un Portfolio`
  
  // Scroll to top on route change
  nextTick(() => {
    window.scrollTo(0, 0)
  })
})
</script>

<style scoped>
/* Navigation styles */
nav {
  backdrop-filter: blur(12px);
  -webkit-backdrop-filter: blur(12px);
}

/* Custom scrollbar for mobile menu */
#mobile-menu {
  scrollbar-width: thin;
  scrollbar-color: #06b6d4 transparent;
}

#mobile-menu::-webkit-scrollbar {
  width: 4px;
}

#mobile-menu::-webkit-scrollbar-track {
  background: transparent;
}

#mobile-menu::-webkit-scrollbar-thumb {
  background-color: #06b6d4;
  border-radius: 2px;
}

/* Page transitions */
.page-enter-active,
.page-leave-active {
  transition: all 0.3s ease;
}

.page-enter-from {
  opacity: 0;
  transform: translateY(20px);
}

.page-leave-to {
  opacity: 0;
  transform: translateY(-20px);
}

/* Fade transition */
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

/* Slide up transition */
.slide-up-enter-active,
.slide-up-leave-active {
  transition: all 0.3s ease;
}

.slide-up-enter-from,
.slide-up-leave-to {
  opacity: 0;
  transform: translateY(20px);
}

/* Focus styles for accessibility */
.focus\:not-sr-only:focus {
  position: absolute !important;
  width: auto !important;
  height: auto !important;
  padding: 0.5rem 1rem !important;
  margin: 0 !important;
  overflow: visible !important;
  clip: auto !important;
  white-space: normal !important;
}

/* Screen reader only */
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  white-space: nowrap;
  border: 0;
}

/* Smooth scrolling */
html {
  scroll-behavior: smooth;
}

/* Custom animations */
@keyframes pulse {
  0%, 100% {
    opacity: 1;
  }
  50% {
    opacity: 0.5;
  }
}

.animate-pulse {
  animation: pulse 2s cubic-bezier(0.4, 0, 0.6, 1) infinite;
}

/* Mobile optimizations */
@media (max-width: 640px) {
  .backdrop-blur-md {
    backdrop-filter: blur(8px);
    -webkit-backdrop-filter: blur(8px);
  }
}

/* Reduce motion for users who prefer it */
@media (prefers-reduced-motion: reduce) {
  *,
  *::before,
  *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
  }
}
</style>