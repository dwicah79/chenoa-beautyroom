<template>
  <nav
    :class="[
      'fixed top-0 left-0 right-0 z-50 transition-all duration-300 overflow-x-hidden',
      isScrolled ? 'bg-white shadow-md' : 'bg-white',
    ]"
  >
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 overflow-x-hidden">
      <div class="flex justify-between items-center h-20">
        <!-- Logo -->
        <a
          href="#hero"
          @click.prevent="scrollToSection('#hero')"
          class="flex items-center space-x-2 cursor-pointer"
          v-motion
          :initial="{ opacity: 0, x: -20 }"
          :visible="{ opacity: 1, x: 0 }"
          :delay="100"
        >
          <span
            :class="[
              'text-2xl font-bold transition-colors',
              isScrolled ? 'text-rose-500' : 'text-rose-500',
            ]"
          >
            Chenoa
          </span>
          <span
            :class="[
              'text-2xl font-light transition-colors',
              isScrolled ? 'text-slate-800' : 'text-slate-800',
            ]"
          >
            Beauty Room
          </span>
        </a>

        <!-- Desktop Menu -->
        <div class="hidden md:flex items-center space-x-8">
          <a
            v-for="(item, index) in menuItems"
            :key="item.name"
            :href="item.href"
            @click.prevent="scrollToSection(item.href)"
            v-motion
            :initial="{ opacity: 0, y: -20 }"
            :visible="{ opacity: 1, y: 0 }"
            :delay="200 + index * 50"
            :class="[
              'text-sm font-medium transition-all duration-300',
              activeSection === item.href
                ? 'text-rose-500 font-semibold'
                : 'text-slate-700 hover:text-rose-500',
            ]"
          >
            {{ item.name }}
          </a>
          <BaseButton
            variant="primary"
            size="sm"
            @click="scrollToSection('#services')"
            v-motion
            :initial="{ opacity: 0, scale: 0.8 }"
            :visible="{ opacity: 1, scale: 1 }"
            :delay="500"
          >
            Booking Sekarang
          </BaseButton>
        </div>

        <!-- Mobile Menu Button -->
        <button
          @click="toggleMobileMenu"
          :class="[
            'md:hidden p-2 rounded-lg transition-colors',
            isScrolled ? 'text-slate-700 hover:bg-slate-100' : 'text-slate-700 hover:bg-slate-100',
          ]"
          aria-label="Toggle menu"
        >
          <svg
            v-if="!isMobileMenuOpen"
            class="w-6 h-6"
            fill="none"
            stroke="currentColor"
            viewBox="0 0 24 24"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M4 6h16M4 12h16M4 18h16"
            />
          </svg>
          <svg v-else class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M6 18L18 6M6 6l12 12"
            />
          </svg>
        </button>
      </div>
    </div>

    <!-- Mobile Menu -->
    <transition
      enter-active-class="transition duration-200 ease-out"
      enter-from-class="opacity-0 scale-95"
      enter-to-class="opacity-100 scale-100"
      leave-active-class="transition duration-100 ease-in"
      leave-from-class="opacity-100 scale-100"
      leave-to-class="opacity-0 scale-95"
    >
      <div v-if="isMobileMenuOpen" class="md:hidden bg-white shadow-lg">
        <div class="px-4 py-6 space-y-4">
          <a
            v-for="item in menuItems"
            :key="item.name"
            :href="item.href"
            @click.prevent="handleMobileMenuClick(item.href)"
            :class="[
              'block font-medium transition-colors',
              activeSection === item.href
                ? 'text-rose-500 font-semibold'
                : 'text-slate-700 hover:text-rose-500',
            ]"
          >
            {{ item.name }}
          </a>
          <BaseButton variant="primary" class="w-full" @click="handleMobileMenuClick('#services')">
            Booking Sekarang
          </BaseButton>
        </div>
      </div>
    </transition>
  </nav>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import BaseButton from '@/components/ui/BaseButton.vue'

const isScrolled = ref(false)
const isMobileMenuOpen = ref(false)
const activeSection = ref('#hero')

const menuItems = [
  { name: 'Beranda', href: '#hero' },
  { name: 'Tentang', href: '#about' },
  { name: 'Layanan', href: '#services' },
  { name: 'Galeri', href: '#gallery' },
  { name: 'Testimoni', href: '#testimonials' },
]

const scrollToSection = (href) => {
  const targetId = href.replace('#', '')
  const targetElement = document.getElementById(targetId)

  if (targetElement) {
    const navbarHeight = 80 // Height of fixed navbar
    const targetPosition = targetElement.offsetTop - navbarHeight

    window.scrollTo({
      top: targetPosition,
      behavior: 'smooth',
    })

    // Update active section immediately
    activeSection.value = href
  }
}

const handleMobileMenuClick = (href) => {
  scrollToSection(href)
  closeMobileMenu()
}

const updateActiveSection = () => {
  const sections = menuItems.map((item) => item.href.replace('#', ''))
  const navbarHeight = 80
  const scrollPosition = window.scrollY + navbarHeight + 100 // Add offset for better detection

  for (let i = sections.length - 1; i >= 0; i--) {
    const section = document.getElementById(sections[i])
    if (section && section.offsetTop <= scrollPosition) {
      activeSection.value = `#${sections[i]}`
      break
    }
  }
}

const handleScroll = () => {
  isScrolled.value = window.scrollY > 50
  updateActiveSection()
}

const toggleMobileMenu = () => {
  isMobileMenuOpen.value = !isMobileMenuOpen.value
}

const closeMobileMenu = () => {
  isMobileMenuOpen.value = false
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
  updateActiveSection() // Set initial active section
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>
