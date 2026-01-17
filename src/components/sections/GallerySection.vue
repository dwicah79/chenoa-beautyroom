<template>
  <section id="gallery" class="py-20 bg-white overflow-hidden">
    <div class="max-w-6xl mx-auto px-4">
      <!-- Section Header -->
      <div
        class="text-center mb-12"
        v-motion
        :initial="{ opacity: 0, y: -30 }"
        :visible="{ opacity: 1, y: 0 }"
      >
        <div
          class="inline-block px-4 py-2 bg-rose-100 text-rose-600 rounded-full text-sm font-semibold mb-4"
        >
          Galeri Kami
        </div>
        <h2 class="text-3xl md:text-4xl font-bold text-slate-800 mb-4">Hasil Karya Terbaik Kami</h2>
        <p class="text-lg text-slate-600 max-w-2xl mx-auto">
          Lihat hasil treatment dari klien-klien kami yang puas
        </p>
      </div>

      <!-- Filter Tabs -->
      <div
        class="flex flex-wrap justify-center gap-3 mb-12"
        v-motion
        :initial="{ opacity: 0, y: 20 }"
        :visible="{ opacity: 1, y: 0 }"
        :delay="100"
      >
        <button
          v-for="filter in filters"
          :key="filter.value"
          @click="activeFilter = filter.value"
          :class="[
            'px-6 py-3 rounded-full font-semibold transition-all duration-300 transform',
            activeFilter === filter.value
              ? 'bg-rose-500 text-white shadow-soft-lg scale-105'
              : 'bg-white text-slate-700 hover:bg-rose-50 border border-rose-100 shadow-soft hover:shadow-soft-lg hover:scale-105',
          ]"
        >
          <span class="relative">
            {{ filter.label }}
            <span
              v-if="activeFilter === filter.value"
              class="absolute -top-1 -right-1 w-2 h-2 bg-rose-100 rounded-full animate-pulse"
            ></span>
          </span>
        </button>
      </div>

      <!-- Gallery Grid -->
      <TransitionGroup
        name="gallery"
        tag="div"
        class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4"
      >
        <div
          v-for="item in filteredGallery"
          :key="`${item.type}-${item.title}`"
          :class="[
            'relative overflow-hidden rounded-xl group cursor-pointer transition-all duration-500',
            item.span ? 'col-span-2 row-span-2' : '',
          ]"
        >
          <div
            :class="[
              'bg-linear-to-br',
              item.color,
              'aspect-square w-full flex items-center justify-center text-white font-semibold',
            ]"
          >
            <div class="text-center">
              <div class="text-2xl mb-2">{{ item.emoji }}</div>
              <div>{{ item.title }}</div>
            </div>
          </div>
          <!-- Overlay -->
          <div
            class="absolute inset-0 bg-black/50 opacity-0 group-hover:opacity-100 transition-opacity duration-300 flex items-center justify-center"
          >
            <div class="text-white text-center p-4">
              <p class="font-semibold">{{ item.title }}</p>
              <p class="text-sm text-gray-200">{{ item.category }}</p>
            </div>
          </div>
        </div>
      </TransitionGroup>
    </div>
  </section>
</template>

<script setup>
import { ref, computed } from 'vue'
import BaseButton from '@/components/ui/BaseButton.vue'

const activeFilter = ref('all')

const filters = [
  { label: 'Semua', value: 'all' },
  { label: 'Nail Art', value: 'nailart' },
  { label: 'Eyelash Extension', value: 'eyelash' },
  { label: 'Lash Lift', value: 'lashlift' },
]

const galleryItems = [
  {
    title: 'Nail Art Classic',
    category: 'Nail Art',
    type: 'nailart',
    emoji: '💅',
    color: 'from-pink-400 to-rose-500',
    span: true,
  },
  {
    title: 'Natural Lash',
    category: 'Lash Lift',
    type: 'lashlift',
    emoji: '✨',
    color: 'from-purple-400 to-pink-500',
  },
  {
    title: 'Volume Lashes',
    category: 'Eyelash Extension',
    type: 'eyelash',
    emoji: '👁️',
    color: 'from-rose-400 to-red-500',
  },
  {
    title: 'French Manicure',
    category: 'Nail Art',
    type: 'nailart',
    emoji: '💖',
    color: 'from-pink-500 to-rose-600',
  },
  {
    title: 'Glitter Nails',
    category: 'Nail Art',
    type: 'nailart',
    emoji: '⭐',
    color: 'from-purple-500 to-pink-600',
  },
  {
    title: 'Classic Lash',
    category: 'Eyelash Extension',
    type: 'eyelash',
    emoji: '👀',
    color: 'from-rose-500 to-pink-600',
    span: true,
  },
  {
    title: 'Mega Volume',
    category: 'Eyelash Extension',
    type: 'eyelash',
    emoji: '💫',
    color: 'from-pink-600 to-purple-600',
  },
  {
    title: 'Ombre Nails',
    category: 'Nail Art',
    type: 'nailart',
    emoji: '🎨',
    color: 'from-rose-600 to-purple-700',
  },
  {
    title: 'Natural Lift',
    category: 'Lash Lift',
    type: 'lashlift',
    emoji: '🌟',
    color: 'from-purple-600 to-pink-700',
  },
  {
    title: 'Acrylic Nails',
    category: 'Nail Art',
    type: 'nailart',
    emoji: '💎',
    color: 'from-pink-700 to-rose-800',
  },
  {
    title: 'Hybrid Lashes',
    category: 'Eyelash Extension',
    type: 'eyelash',
    emoji: '✨',
    color: 'from-rose-700 to-purple-800',
  },
  {
    title: 'Keratin Lift',
    category: 'Lash Lift',
    type: 'lashlift',
    emoji: '💫',
    color: 'from-purple-700 to-pink-800',
  },
]

const filteredGallery = computed(() => {
  if (activeFilter.value === 'all') {
    return galleryItems
  }
  return galleryItems.filter((item) => item.type === activeFilter.value)
})
</script>

<style scoped>
/* Gallery transition animations */
.gallery-enter-active {
  transition: all 0.5s ease;
}

.gallery-leave-active {
  transition: all 0.3s ease;
}

.gallery-enter-from {
  opacity: 0;
  transform: scale(0.8) translateY(20px);
}

.gallery-leave-to {
  opacity: 0;
  transform: scale(0.8) translateY(-20px);
}

/* Stagger animation - delay berdasarkan posisi */
.gallery-enter-active:nth-child(1) {
  transition-delay: 0ms;
}
.gallery-enter-active:nth-child(2) {
  transition-delay: 50ms;
}
.gallery-enter-active:nth-child(3) {
  transition-delay: 100ms;
}
.gallery-enter-active:nth-child(4) {
  transition-delay: 150ms;
}
.gallery-enter-active:nth-child(5) {
  transition-delay: 200ms;
}
.gallery-enter-active:nth-child(6) {
  transition-delay: 250ms;
}
.gallery-enter-active:nth-child(7) {
  transition-delay: 300ms;
}
.gallery-enter-active:nth-child(8) {
  transition-delay: 350ms;
}
.gallery-enter-active:nth-child(9) {
  transition-delay: 400ms;
}
.gallery-enter-active:nth-child(10) {
  transition-delay: 450ms;
}
.gallery-enter-active:nth-child(11) {
  transition-delay: 500ms;
}
.gallery-enter-active:nth-child(12) {
  transition-delay: 550ms;
}

/* Move animation - untuk smooth repositioning */
.gallery-move {
  transition: transform 0.5s ease;
}
</style>
