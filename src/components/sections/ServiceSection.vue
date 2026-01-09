<template>
  <section id="services" class="py-20 bg-gray-50">
    <div class="max-w-6xl mx-auto px-4">
      <!-- Section Header -->
      <div
        class="text-center mb-16"
        v-motion
        :initial="{ opacity: 0, y: -30 }"
        :visible="{ opacity: 1, y: 0 }"
        :duration="800"
      >
        <div
          class="inline-block px-4 py-2 bg-rose-100 text-rose-600 rounded-full text-sm font-semibold mb-4"
        >
          Layanan Kami
        </div>
        <h2 class="text-3xl md:text-4xl font-bold text-gray-900 mb-4">
          Layanan Kecantikan Profesional
        </h2>
        <p class="text-lg text-gray-600 max-w-2xl mx-auto">
          Kami menawarkan berbagai layanan kecantikan dengan standar profesional dan hasil terbaik
        </p>
      </div>

      <!-- Services Grid -->
      <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
        <ServiceCard
          v-for="(service, index) in services"
          :key="service.title"
          :service="service"
          :delay="index * 100"
        />
      </div>

      <!-- CTA -->
      <div
        class="text-center mt-12"
        v-motion
        :initial="{ opacity: 0, y: 20 }"
        :visible="{ opacity: 1, y: 0 }"
        :delay="400"
      >
        <BaseButton size="lg" variant="primary"> Lihat Semua Layanan </BaseButton>
      </div>
    </div>
  </section>
</template>

<script setup>
import ServiceCard from '@/components/ui/ServiceCard.vue'
import BaseButton from '@/components/ui/BaseButton.vue'

const services = [
  {
    title: 'Nail Art',
    description:
      'Perawatan kuku artistik dengan berbagai design custom. Hasil rapi, cantik, dan tahan lama hingga 2-3 minggu.',
    price: 'Mulai dari Rp 75.000',
    icon: `
      <svg class="w-8 h-8" fill="none" stroke="currentColor" viewBox="0 0 24 24">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M7 21a4 4 0 01-4-4V5a2 2 0 012-2h4a2 2 0 012 2v12a4 4 0 01-4 4zm0 0h12a2 2 0 002-2v-4a2 2 0 00-2-2h-2.343M11 7.343l1.657-1.657a2 2 0 012.828 0l2.829 2.829a2 2 0 010 2.828l-8.486 8.485M7 17h.01"/>
      </svg>
    `,
    features: ['Design Custom', 'Cat Gel Premium', 'Tahan Lama', 'Hasil Rapi'],
  },
  {
    title: 'Lash Lift',
    description:
      'Lash lift natural untuk tampilan mata lebih segar tanpa maskara. Bulu mata tampak lebih lentik dan panjang.',
    price: 'Mulai dari Rp 150.000',
    icon: `
      <svg class="w-8 h-8" fill="none" stroke="currentColor" viewBox="0 0 24 24">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 12a3 3 0 11-6 0 3 3 0 016 0z"/>
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M2.458 12C3.732 7.943 7.523 5 12 5c4.478 0 8.268 2.943 9.542 7-1.274 4.057-5.064 7-9.542 7-4.477 0-8.268-2.943-9.542-7z"/>
      </svg>
    `,
    features: ['Tampilan Natural', 'Tahan 6-8 Minggu', 'Tanpa Ekstensi', 'Perawatan Mudah'],
  },
  {
    title: 'Eyelash Extension',
    description:
      'Eyelash extension profesional untuk mata lebih tegas dan menawan. Tersedia berbagai jenis dan volume.',
    price: 'Mulai dari Rp 200.000',
    icon: `
      <svg class="w-8 h-8" fill="none" stroke="currentColor" viewBox="0 0 24 24">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 3v4M3 5h4M6 17v4m-2-2h4m5-16l2.286 6.857L21 12l-5.714 2.143L13 21l-2.286-6.857L5 12l5.714-2.143L13 3z"/>
      </svg>
    `,
    features: ['Natural & Volume', 'Bahan Premium', 'Tahan 3-4 Minggu', 'Waterproof'],
  },
]
</script>
