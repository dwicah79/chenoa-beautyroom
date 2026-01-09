<template>
  <section id="gallery" class="py-20 bg-gray-50">
    <div class="max-w-6xl mx-auto px-4">
      <!-- Section Header -->
      <div
        class="text-center mb-16"
        v-motion
        :initial="{ opacity: 0, y: -30 }"
        :visible="{ opacity: 1, y: 0 }"
      >
        <div
          class="inline-block px-4 py-2 bg-rose-100 text-rose-600 rounded-full text-sm font-semibold mb-4"
        >
          Galeri Kami
        </div>
        <h2 class="text-3xl md:text-4xl font-bold text-gray-900 mb-4">Hasil Karya Terbaik Kami</h2>
        <p class="text-lg text-gray-600 max-w-2xl mx-auto">
          Lihat hasil treatment dari klien-klien kami yang puas
        </p>
      </div>

      <!-- Gallery Grid -->
      <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4">
        <div
          v-for="(item, index) in galleryItems"
          :key="index"
          :class="[
            'relative overflow-hidden rounded-xl group cursor-pointer',
            item.span ? 'col-span-2 row-span-2' : '',
          ]"
          v-motion
          :initial="{ opacity: 0, scale: 0.9 }"
          :visible="{ opacity: 1, scale: 1 }"
          :delay="index * 50"
        >
          <div
            :class="[
              'bg-gradient-to-br',
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
      </div>

      <!-- View More -->
      <div
        class="text-center mt-12"
        v-motion
        :initial="{ opacity: 0, y: 20 }"
        :visible="{ opacity: 1, y: 0 }"
        :delay="400"
      >
        <BaseButton size="lg" variant="outline"> Lihat Semua Galeri </BaseButton>
      </div>
    </div>
  </section>
</template>

<script setup>
import BaseButton from '@/components/ui/BaseButton.vue'

const galleryItems = [
  {
    title: 'Nail Art Classic',
    category: 'Nail Art',
    emoji: '💅',
    color: 'from-pink-400 to-rose-500',
    span: true,
  },
  {
    title: 'Natural Lash',
    category: 'Lash Lift',
    emoji: '✨',
    color: 'from-purple-400 to-pink-500',
  },
  {
    title: 'Volume Lashes',
    category: 'Eyelash Extension',
    emoji: '👁️',
    color: 'from-rose-400 to-red-500',
  },
  {
    title: 'French Manicure',
    category: 'Nail Art',
    emoji: '💖',
    color: 'from-pink-500 to-rose-600',
  },
  {
    title: 'Glitter Nails',
    category: 'Nail Art',
    emoji: '⭐',
    color: 'from-purple-500 to-pink-600',
  },
  {
    title: 'Classic Lash',
    category: 'Eyelash Extension',
    emoji: '👀',
    color: 'from-rose-500 to-pink-600',
    span: true,
  },
  {
    title: 'Mega Volume',
    category: 'Eyelash Extension',
    emoji: '💫',
    color: 'from-pink-600 to-purple-600',
  },
  { title: 'Ombre Nails', category: 'Nail Art', emoji: '🎨', color: 'from-rose-600 to-purple-700' },
]
</script>
