<template>
  <section class="min-h-screen bg-gradient-to-br from-gray-50 to-blue-50 py-16 sm:py-20 px-4 sm:px-6">
    <div class="max-w-6xl mx-auto">
      <!-- Header -->
      <div class="text-center mb-12 sm:mb-16" ref="headerSection">
        <h1 class="text-3xl sm:text-4xl md:text-5xl font-bold text-gray-800 mb-4">
          Get In <span class="text-blue-600">Touch</span>
        </h1>
        <p class="text-gray-600 max-w-2xl mx-auto text-lg">
          Have a project in mind or want to collaborate? I'd love to hear from you. 
          Let's discuss how we can work together to bring your ideas to life.
        </p>
        <div class="w-24 h-1 bg-gradient-to-r from-blue-600 to-cyan-600 mx-auto rounded-full mt-6"></div>
      </div>

      <div class="grid lg:grid-cols-2 gap-6 lg:gap-12 items-start">
        <!-- Contact Information -->
        <div class="space-y-8" ref="contactInfoSection">
          <!-- Personal Info Card -->
          <div class="bg-white rounded-2xl shadow-lg p-6 sm:p-8 hover:shadow-xl transition-shadow duration-300">
            <h3 class="text-2xl font-bold text-gray-800 mb-6 flex items-center">
              <div class="w-8 h-8 bg-blue-600 rounded-full flex items-center justify-center mr-3">
                <svg class="w-4 h-4 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M16 7a4 4 0 11-8 0 4 4 0 018 0zM12 14a7 7 0 00-7 7h14a7 7 0 00-7-7z" />
                </svg>
              </div>
              Contact Information
            </h3>
            
            <div class="space-y-6 sm:space-y-8">
              <!-- Email -->
              <div class="flex items-center space-x-4">
                <div class="w-10 h-10 sm:w-12 sm:h-12 bg-blue-100 rounded-full flex items-center justify-center">
                  <svg class="w-6 h-6 text-blue-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 4.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z" />
                  </svg>
                </div>
                <div>
                  <p class="text-sm text-gray-500">Email</p>
                  <a href="mailto:mean.un@student.passerellesnumeriques.org" class="font-semibold text-gray-800 hover:text-blue-600 transition-colors">
                    mean.un@student.passerellesnumeriques.org
                  </a>
                </div>
              </div>

              <!-- Phone -->
              <div class="flex items-center space-x-4">
                <div class="w-10 h-10 sm:w-12 sm:h-12 bg-green-100 rounded-full flex items-center justify-center">
                  <svg class="w-6 h-6 text-green-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z" />
                  </svg>
                </div>
                <div>
                  <p class="text-sm text-gray-500">Phone</p>
                  <a href="tel:+85597920150" class="font-semibold text-gray-800 hover:text-green-600 transition-colors">
                    +855 97 920 1500
                  </a>
                </div>
              </div>

              <!-- Location -->
              <div class="flex items-center space-x-4">
                <div class="w-10 h-10 sm:w-12 sm:h-12 bg-purple-100 rounded-full flex items-center justify-center">
                  <svg class="w-6 h-6 text-purple-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z" />
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z" />
                  </svg>
                </div>
                <div>
                  <p class="text-sm text-gray-500">Location</p>
                  <p class="font-semibold text-gray-800">
                    Phnom Penh, Cambodia
                  </p>
                  <p class="text-xs text-gray-500 mt-1">
                    BP511 St. 371, Sangkat Tek Thla, Khan Sen Sok
                  </p>
                </div>
              </div>
            </div>
          </div>

          <!-- Social Links -->
          <div class="bg-white rounded-2xl shadow-lg p-6 sm:p-8 hover:shadow-xl transition-shadow duration-300">
            <h3 class="text-xl font-bold text-gray-800 mb-6">Connect With Me</h3>
            <div class="grid grid-cols-1 sm:grid-cols-2 gap-3 sm:gap-4">
              <a 
                v-for="social in socialLinks" 
                :key="social.name"
                :href="social.url" 
                target="_blank" 
                rel="noopener noreferrer"
                class="flex items-center space-x-3 p-4 rounded-lg border border-gray-200 hover:border-blue-300 hover:bg-blue-50 transition-all duration-300 group"
              >
                <div class="w-8 h-8 rounded-full flex items-center justify-center" :class="social.bgColor">
                  <div v-html="social.icon" class="w-4 h-4 text-white"></div>
                </div>
                <span class="font-medium text-gray-700 group-hover:text-blue-600 transition-colors">{{ social.name }}</span>
              </a>
            </div>
          </div>

          <!-- Availability Status -->
          <div class="bg-gradient-to-r from-green-500 to-emerald-500 rounded-2xl shadow-lg p-8 text-white">
            <div class="flex items-center mb-4">
              <div class="w-3 h-3 bg-white rounded-full animate-pulse mr-3"></div>
              <h3 class="text-xl font-bold">Currently Available</h3>
            </div>
            <p class="opacity-90 mb-4">
              I'm actively looking for internship opportunities and freelance projects. 
              Currently studying at PNC and available for part-time work.
            </p>
            <div class="flex items-center text-sm opacity-80">
              <svg class="w-4 h-4 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z" />
              </svg>
              Response time: Within 24 hours
            </div>
          </div>
        </div>

        <!-- Contact Form -->
        <div class="bg-white rounded-2xl shadow-lg p-6 sm:p-8 hover:shadow-xl transition-shadow duration-300" ref="formSection">
          <h3 class="text-2xl font-bold text-gray-800 mb-6">Send Me a Message</h3>
          
          <form @submit.prevent="handleSubmit" class="space-y-6">
            <!-- Name Input -->
            <div>
              <label for="name" class="block text-sm font-medium text-gray-700 mb-2">
                Full Name *
              </label>
              <input
                id="name"
                v-model="form.name"
                type="text"
                name="name"
                required
                class="w-full px-3 sm:px-4 py-2 sm:py-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-transparent transition-all duration-300"
                placeholder="Enter your full name"
              />
            </div>

            <!-- Email Input -->
            <div>
              <label for="email" class="block text-sm font-medium text-gray-700 mb-2">
                Email Address *
              </label>
              <input
                id="email"
                v-model="form.email"
                type="email"
                name="email"
                required
                class="w-full px-3 sm:px-4 py-2 sm:py-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-transparent transition-all duration-300"
                placeholder="Enter your email address"
              />
            </div>

            <!-- Subject Input -->
            <div>
              <label for="subject" class="block text-sm font-medium text-gray-700 mb-2">
                Subject
              </label>
              <select
                id="subject"
                v-model="form.subject"
                class="w-full px-3 sm:px-4 py-2 sm:py-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-transparent transition-all duration-300"
              >
                <option value="">Select a subject</option>
                <option value="project">Project Collaboration</option>
                <option value="internship">Internship Opportunity</option>
                <option value="freelance">Freelance Work</option>
                <option value="consultation">Technical Consultation</option>
                <option value="other">Other</option>
              </select>
            </div>

            <!-- Message Input -->
            <div>
              <label for="message" class="block text-sm font-medium text-gray-700 mb-2">
                Message *
              </label>
              <textarea
                id="message"
                v-model="form.message"
                name="message"
                required
                rows="6"
                class="w-full px-3 sm:px-4 py-2 sm:py-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-transparent transition-all duration-300 resize-none"
                placeholder="Tell me about your project or how I can help you..."
              ></textarea>
            </div>

            <!-- Submit Button -->
            <button
              type="submit"
              :disabled="isSubmitting"
              class="w-full bg-gradient-to-r from-blue-600 to-cyan-600 text-white font-semibold py-4 px-6 rounded-lg shadow-lg hover:shadow-xl transform hover:-translate-y-1 transition-all duration-300 disabled:opacity-50 disabled:cursor-not-allowed disabled:transform-none text-sm sm:text-base"
            >
              <span v-if="!isSubmitting" class="flex items-center justify-center">
                Send Message
                <svg class="w-5 h-5 ml-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 19l9 2-9-18-9 18 9-2zm0 0v-8" />
                </svg>
              </span>
              <span v-else class="flex items-center justify-center">
                <svg class="animate-spin -ml-1 mr-3 h-5 w-5 text-white" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24">
                  <circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4"></circle>
                  <path class="opacity-75" fill="currentColor" d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z"></path>
                </svg>
                Sending...
              </span>
            </button>
          </form>

          <!-- Success/Error Messages -->
          <div v-if="submitMessage" class="mt-6 p-4 rounded-lg" :class="submitSuccess ? 'bg-green-100 text-green-800' : 'bg-red-100 text-red-800'">
            <div class="flex items-center">
              <svg v-if="submitSuccess" class="w-5 h-5 mr-2" fill="currentColor" viewBox="0 0 20 20">
                <path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z" clip-rule="evenodd" />
              </svg>
              <svg v-else class="w-5 h-5 mr-2" fill="currentColor" viewBox="0 0 20 20">
                <path fill-rule="evenodd" d="M18 10a8 8 0 11-16 0 8 8 0 0116 0zm-7 4a1 1 0 11-2 0 1 1 0 012 0zm-1-9a1 1 0 00-1 1v4a1 1 0 102 0V6a1 1 0 00-1-1z" clip-rule="evenodd" />
              </svg>
              {{ submitMessage }}
            </div>
          </div>
        </div>
      </div>

      <!-- FAQ Section -->
      <div class="mt-20 bg-white rounded-2xl shadow-lg p-6 sm:p-8 lg:p-12" ref="faqSection">
        <div class="text-center mb-12">
          <h2 class="text-3xl font-bold text-gray-800 mb-4">Frequently Asked Questions</h2>
          <p class="text-gray-600">Quick answers to common questions about working with me.</p>
        </div>

        <div class="grid md:grid-cols-2 gap-6 sm:gap-8">
          <div v-for="faq in faqs" :key="faq.question" class="space-y-4">
            <h3 class="text-base sm:text-lg font-semibold text-gray-800">{{ faq.question }}</h3>
            <p class="text-gray-600">{{ faq.answer }}</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { reactive, ref, onMounted } from 'vue'
import ScrollReveal from 'scrollreveal'

// Template refs
const headerSection = ref(null)
const contactInfoSection = ref(null)
const formSection = ref(null)
const faqSection = ref(null)

// Form state
const form = reactive({
  name: '',
  email: '',
  subject: '',
  message: ''
})

const isSubmitting = ref(false)
const submitMessage = ref('')
const submitSuccess = ref(false)

// Social links
const socialLinks = [
  {
    name: 'GitHub',
    url: 'https://github.com/Mean-UN',
    icon: `<svg fill="currentColor" viewBox="0 0 24 24"><path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/></svg>`,
    bgColor: 'bg-gray-800'
  },
  {
    name: 'LinkedIn',
    url: 'linkedin.com/in/mean-un-personal',
    icon: `<svg fill="currentColor" viewBox="0 0 24 24"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg>`,
    bgColor: 'bg-blue-600'
  },
  {
    name: 'Telegram',
    url: 'https://t.me/Mean_Un',
    icon: `<svg fill="currentColor" viewBox="0 0 24 24"><path d="M11.944 0A12 12 0 0 0 0 12a12 12 0 0 0 12 12 12 12 0 0 0 12-12A12 12 0 0 0 12 0a12 12 0 0 0-.056 0zm4.962 7.224c.1-.002.321.023.465.14a.506.506 0 0 1 .171.325c.016.093.036.306.02.472-.18 1.898-.962 6.502-1.36 8.627-.168.9-.499 1.201-.82 1.23-.696.065-1.225-.46-1.9-.902-1.056-.693-1.653-1.124-2.678-1.8-1.185-.78-.417-1.21.258-1.91.177-.184 3.247-2.977 3.307-3.23.007-.032.014-.15-.056-.212s-.174-.041-.249-.024c-.106.024-1.793 1.14-5.061 3.345-.48.33-.913.49-1.302.48-.428-.008-1.252-.241-1.865-.44-.752-.245-1.349-.374-1.297-.789.027-.216.325-.437.893-.663 3.498-1.524 5.83-2.529 6.998-3.014 3.332-1.386 4.025-1.627 4.476-1.635z"/></svg>`,
    bgColor: 'bg-blue-500'
  },
  {
    name: 'Portfolio',
    url: '#',
    icon: `<svg fill="currentColor" viewBox="0 0 24 24"><path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/></svg>`,
    bgColor: 'bg-purple-600'
  }
]

// FAQ data
const faqs = [
  {
    question: 'What services do you offer?',
    answer: 'I specialize in full-stack web development, including frontend (HTML, CSS, JavaScript, Vue.js), backend (PHP, Laravel, Node.js), and database design (MySQL). I also offer UI/UX design services using Figma.'
  },
  {
    question: 'What is your availability?',
    answer: 'I\'m currently a student at PNC, so I\'m available for part-time projects and internships. I can dedicate 20-30 hours per week to client work and respond to messages within 24 hours.'
  },
  {
    question: 'Do you work on team projects?',
    answer: 'I have experience working in teams of 3-6 people on various projects. I\'m comfortable using collaboration tools like GitHub, Jira, and Figma for team coordination.'
  },
  {
    question: 'What is your preferred communication method?',
    answer: 'I prefer email for formal communications and project discussions. For quick questions or updates, you can reach me via Telegram or phone. I also use video calls for project planning and reviews.'
  }
]

// Form submission handler
async function handleSubmit() {
  isSubmitting.value = true
  submitMessage.value = ''
  
  try {
    // Simulate API call - replace with actual endpoint
    await new Promise(resolve => setTimeout(resolve, 2000))
    
    // For now, we'll simulate a successful submission
    // In a real app, you'd send this to your backend
    console.log('Form submitted:', form)
    
    submitSuccess.value = true
    submitMessage.value = 'Thank you for your message! I\'ll get back to you within 24 hours.'
    
    // Reset form
    Object.keys(form).forEach(key => {
      form[key] = ''
    })
    
  } catch (error) {
    submitSuccess.value = false
    submitMessage.value = 'Sorry, there was an error sending your message. Please try again or contact me directly via email.'
  } finally {
    isSubmitting.value = false
    
    // Clear message after 5 seconds
    setTimeout(() => {
      submitMessage.value = ''
    }, 5000)
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
  sr.reveal(contactInfoSection.value, { delay: 400 })
  sr.reveal(formSection.value, { delay: 600 })
  sr.reveal(faqSection.value, { delay: 800 })
})
</script>

<style scoped>
/* Custom animations */
@keyframes pulse {
  0%, 100% { opacity: 1; }
  50% { opacity: 0.5; }
}

.animate-pulse {
  animation: pulse 2s cubic-bezier(0.4, 0, 0.6, 1) infinite;
}

/* Form focus styles */
input:focus, textarea:focus, select:focus {
  box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.1);
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

/* Mobile-specific styles */
@media (max-width: 640px) {
  .flex.items-center.space-x-4 {
    margin-bottom: 1rem; /* Add spacing between contact info items */
  }

  .text-sm {
    font-size: 0.9rem; /* Improve readability on smaller screens */
  }

  .font-semibold {
    font-weight: 600; /* Slightly bolder for better visibility */
  }
}
</style>
