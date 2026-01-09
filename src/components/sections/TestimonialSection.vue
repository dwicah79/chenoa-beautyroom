<template>
  <section id="testimonials" class="py-20 bg-white">
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
          Testimoni Klien
        </div>
        <h2 class="text-3xl md:text-4xl font-bold text-gray-900 mb-4">
          Apa Kata Mereka Tentang Kami
        </h2>
        <p class="text-lg text-gray-600 max-w-2xl mx-auto">
          Dengarkan pengalaman klien-klien kami yang puas dengan layanan Chenoa Beauty Room
        </p>
      </div>

      <!-- Testimonials Grid -->
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
        <div
          v-for="(testimonial, index) in testimonials"
          :key="testimonial.name"
          class="bg-gradient-to-br from-rose-50 to-purple-50 rounded-2xl p-6 shadow-lg hover:shadow-xl transition-all duration-300"
          v-motion
          :initial="{ opacity: 0, y: 30 }"
          :visible="{ opacity: 1, y: 0 }"
          :delay="index * 100"
        >
          <!-- Stars -->
          <div class="flex gap-1 mb-4">
            <svg
              v-for="i in 5"
              :key="i"
              class="w-5 h-5 text-yellow-400"
              fill="currentColor"
              viewBox="0 0 20 20"
            >
              <path
                d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z"
              />
            </svg>
          </div>

          <!-- Review -->
          <p class="text-gray-700 mb-6 italic">"{{ testimonial.review }}"</p>

          <!-- Author -->
          <div class="flex items-center gap-4">
            <div
              class="w-12 h-12 bg-gradient-to-br from-rose-400 to-purple-400 rounded-full flex items-center justify-center text-white font-bold text-lg"
            >
              {{ testimonial.initial }}
            </div>
            <div>
              <div class="font-semibold text-gray-900">{{ testimonial.name }}</div>
              <div class="text-sm text-gray-600">{{ testimonial.service }}</div>
            </div>
          </div>
        </div>
      </div>

      <!-- Rating Summary -->
      <div
        class="mt-16 bg-gradient-to-r from-rose-600 to-purple-600 rounded-2xl p-8 text-white text-center"
        v-motion
        :initial="{ opacity: 0, y: 30 }"
        :visible="{ opacity: 1, y: 0 }"
        :delay="400"
      >
        <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
          <div>
            <div class="text-5xl font-bold mb-2">4.9</div>
            <div class="text-rose-100">Rating Rata-rata</div>
          </div>
          <div>
            <div class="text-5xl font-bold mb-2">500+</div>
            <div class="text-rose-100">Klien Puas</div>
          </div>
          <div>
            <div class="text-5xl font-bold mb-2">127</div>
            <div class="text-rose-100">Total Ulasan</div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const testimonials = [
  {
    name: 'Sarah Wijaya',
    initial: 'S',
    service: 'Nail Art',
    review:
      'Hasilnya sangat rapi dan tahan lama! Design nail art nya juga cantik banget. Recommended!',
  },
  {
    name: 'Diana Putri',
    initial: 'D',
    service: 'Lash Lift',
    review:
      'Bulu mata jadi lebih lentik natural. Gak perlu pakai maskara lagi setiap hari. Love it!',
  },
  {
    name: 'Melissa Tan',
    initial: 'M',
    service: 'Eyelash Extension',
    review:
      'Pelayanan ramah dan profesional. Hasil extension nya natural banget, sesuai yang aku mau.',
  },
  {
    name: 'Amanda Chen',
    initial: 'A',
    service: 'Nail Art',
    review: 'Tempatnya nyaman, bersih, dan terapis nya sangat teliti. Pasti balik lagi!',
  },
  {
    name: 'Rina Sari',
    initial: 'R',
    service: 'Lash Lift',
    review: 'Pertama kali lash lift dan hasilnya melebihi ekspektasi. Mata jadi lebih fresh!',
  },
  {
    name: 'Jessica Lee',
    initial: 'J',
    service: 'Eyelash Extension',
    review: 'Sudah langganan disini. Hasilnya selalu konsisten bagus dan harganya worth it!',
  },
]
</script>
