<template>
  <section id="cta" class="py-20 bg-white overflow-hidden">
    <div class="max-w-6xl mx-auto px-4">
      <div
        class="text-center"
        v-motion
        :initial="{ opacity: 0, y: 30 }"
        :visible="{ opacity: 1, y: 0 }"
        :duration="800"
      >
        <h2 class="text-3xl md:text-4xl lg:text-5xl font-bold text-neutral-800 mb-6">
          Siap Tampil Lebih Cantik dan Percaya Diri?
        </h2>
        <p class="text-xl md:text-2xl text-neutral-600 mb-8 max-w-3xl mx-auto">
          Booking sekarang dan dapatkan konsultasi gratis untuk treatment pertama Anda
        </p>

        <!-- Features -->
        <div
          class="grid grid-cols-1 md:grid-cols-3 gap-6 mb-12 max-w-4xl mx-auto"
          v-motion
          :initial="{ opacity: 0, y: 20 }"
          :visible="{ opacity: 1, y: 0 }"
          :delay="200"
        >
          <div
            v-for="(feature, index) in features"
            :key="feature.title"
            class="bg-neutral-50 rounded-xl p-6 border border-neutral-200"
            v-motion
            :initial="{ opacity: 0, scale: 0.9 }"
            :visible="{ opacity: 1, scale: 1 }"
            :delay="300 + index * 100"
          >
            <div
              class="w-12 h-12 bg-rose-100 rounded-full flex items-center justify-center mx-auto mb-4"
            >
              <div v-html="feature.icon" class="text-rose-600"></div>
            </div>
            <h3 class="font-semibold text-lg mb-2 text-neutral-800">{{ feature.title }}</h3>
            <p class="text-neutral-600 text-sm">{{ feature.description }}</p>
          </div>
        </div>

        <!-- CTA Buttons -->
        <div
          class="flex flex-col sm:flex-row gap-4 justify-center items-center"
          v-motion
          :initial="{ opacity: 0, y: 20 }"
          :visible="{ opacity: 1, y: 0 }"
          :delay="600"
        >
          <BookingButton variant="primary" size="lg"> Booking via WhatsApp </BookingButton>
        </div>

        <!-- Additional Info -->
        <div
          class="mt-8 text-neutral-600"
          v-motion
          :initial="{ opacity: 0 }"
          :visible="{ opacity: 1 }"
          :delay="800"
        >
          <p class="text-sm">⭐ Promo Special: Diskon 20% untuk pelanggan baru!</p>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import BookingButton from '@/components/ui/BookingButton.vue'

const features = [
  {
    title: 'Konsultasi Gratis',
    description: 'Dapatkan konsultasi treatment yang sesuai',
    icon: `<svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 10h.01M12 10h.01M16 10h.01M9 16H5a2 2 0 01-2-2V6a2 2 0 012-2h14a2 2 0 012 2v8a2 2 0 01-2 2h-5l-5 5v-5z"/>
    </svg>`,
  },
  {
    title: 'Booking Mudah',
    description: 'Reservasi langsung via WhatsApp',
    icon: `<svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z"/>
    </svg>`,
  },
  {
    title: 'Promo Menarik',
    description: 'Dapatkan diskon spesial hari ini',
    icon: `<svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8c-1.657 0-3 .895-3 2s1.343 2 3 2 3 .895 3 2-1.343 2-3 2m0-8c1.11 0 2.08.402 2.599 1M12 8V7m0 1v8m0 0v1m0-1c-1.11 0-2.08-.402-2.599-1M21 12a9 9 0 11-18 0 9 9 0 0118 0z"/>
    </svg>`,
  },
]
</script>
