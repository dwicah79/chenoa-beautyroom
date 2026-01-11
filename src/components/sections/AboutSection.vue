<template>
  <section id="about" class="py-20 bg-white">
    <div class="max-w-7xl mx-auto px-4">
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-12 items-center">
        <!-- Image -->
        <div
          class="relative order-2 lg:order-1"
          v-motion
          :initial="{ opacity: 0, x: -50 }"
          :visible="{ opacity: 1, x: 0 }"
          :duration="800"
        >
          <div class="relative aspect-[4/3] rounded-3xl overflow-hidden shadow-2xl">
            <div class="absolute inset-0 bg-gradient-to-br from-rose-300 to-purple-300">
              <img src="../../assets/images/testi4.jpg" class="object-cover" alt="" />
            </div>
          </div>

          <!-- Decorative Element -->
          <div class="absolute -bottom-6 -right-6 w-32 h-32 bg-rose-100 rounded-full -z-10"></div>
          <div class="absolute -top-6 -left-6 w-24 h-24 bg-purple-100 rounded-full -z-10"></div>
        </div>

        <!-- Content -->
        <div
          class="order-1 lg:order-2"
          v-motion
          :initial="{ opacity: 0, x: 50 }"
          :visible="{ opacity: 1, x: 0 }"
          :duration="800"
          :delay="200"
        >
          <div
            class="inline-block px-4 py-2 bg-rose-100 text-rose-600 rounded-full text-sm font-semibold mb-4"
          >
            Tentang Kami
          </div>
          <h2 class="text-3xl md:text-4xl font-bold text-gray-900 mb-6">
            Karena Setiap Wanita Pantas Merasa Cantik Setiap Hari
          </h2>
          <p class="text-lg text-gray-600 mb-6">
            Chenoa Beauty Room hadir untuk memberikan pengalaman kecantikan yang tak terlupakan.
            Kami berkomitmen memberikan layanan terbaik dengan hasil yang memuaskan.
          </p>
          <p class="text-lg text-gray-600 mb-8">
            Dengan terapis profesional dan produk berkualitas tinggi, kami memastikan setiap
            treatment yang Anda dapatkan memberikan hasil maksimal dan pengalaman yang menyenangkan.
          </p>

          <!-- Features -->
          <div class="grid grid-cols-1 sm:grid-cols-2 gap-6">
            <div
              v-for="(feature, index) in features"
              :key="feature.title"
              class="flex items-start gap-3"
              v-motion
              :initial="{ opacity: 0, y: 20 }"
              :visible="{ opacity: 1, y: 0 }"
              :delay="400 + index * 100"
            >
              <div
                class="flex-shrink-0 w-10 h-10 bg-rose-100 rounded-lg flex items-center justify-center"
              >
                <svg
                  class="w-6 h-6 text-rose-600"
                  fill="none"
                  stroke="currentColor"
                  viewBox="0 0 24 24"
                >
                  <path
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    stroke-width="2"
                    d="M5 13l4 4L19 7"
                  />
                </svg>
              </div>
              <div>
                <h3 class="font-semibold text-gray-900 mb-1">{{ feature.title }}</h3>
                <p class="text-sm text-gray-600">{{ feature.description }}</p>
              </div>
            </div>
          </div>

          <div class="mt-8">
            <BaseButton size="lg" variant="primary"> Booking Sekarang </BaseButton>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import BaseButton from '@/components/ui/BaseButton.vue'

const features = [
  {
    title: 'Terapis Profesional',
    description: 'Tim berpengalaman dan tersertifikasi',
  },
  {
    title: 'Produk Berkualitas',
    description: 'Menggunakan produk premium terbaik',
  },
  {
    title: 'Hasil Natural',
    description: 'Tampilan alami dan menawan',
  },
  {
    title: 'Harga Terjangkau',
    description: 'Kualitas premium dengan harga bersahabat',
  },
]
</script>
