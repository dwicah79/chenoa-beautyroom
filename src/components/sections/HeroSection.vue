<template>
  <section
    id="hero"
    class="relative min-h-screen flex items-center justify-center overflow-hidden bg-gradient-to-br from-rose-50 via-pink-50 to-purple-50"
  >
    <!-- Background Decoration -->
    <div class="absolute inset-0 overflow-hidden">
      <div
        class="absolute -top-1/2 -right-1/2 w-full h-full bg-rose-200/20 rounded-full blur-3xl"
      ></div>
      <div
        class="absolute -bottom-1/2 -left-1/2 w-full h-full bg-purple-200/20 rounded-full blur-3xl"
      ></div>
    </div>

    <!-- Content -->
    <div class="relative z-10 w-full px-4 py-20">
      <div class="max-w-7xl mx-auto">
        <div class="grid grid-cols-1 lg:grid-cols-2 gap-12 items-center">
          <!-- Text Content -->
          <div
            class="text-center lg:text-left"
            v-motion
            :initial="{ opacity: 0, x: -50 }"
            :visible="{ opacity: 1, x: 0 }"
            :duration="800"
          >
            <h1 class="text-4xl md:text-5xl lg:text-6xl font-bold text-gray-900 mb-6 leading-tight">
              Tampil Lebih
              <span class="text-rose-600"> Percaya Diri</span>
              dengan Perawatan Terbaik
            </h1>
            <p class="text-lg md:text-xl text-gray-600 mb-8 max-w-2xl mx-auto lg:mx-0">
              Chenoa Beauty Room menyediakan layanan Nail Art, Lash Lift, dan Eyelash Extension
              profesional dengan hasil natural, rapi, dan tahan lama.
            </p>
            <div class="flex flex-col sm:flex-row gap-4 justify-center lg:justify-start">
              <BaseButton size="lg" variant="primary"> Booking Sekarang </BaseButton>
              <BaseButton size="lg" variant="outline"> Lihat Layanan </BaseButton>
            </div>

            <!-- Stats -->
            <div
              class="grid grid-cols-3 gap-6 mt-12"
              v-motion
              :initial="{ opacity: 0, y: 20 }"
              :visible="{ opacity: 1, y: 0 }"
              :delay="400"
            >
              <div class="text-center lg:text-left">
                <div class="text-3xl font-bold text-rose-600">500+</div>
                <div class="text-sm text-gray-600">Klien Puas</div>
              </div>
              <div class="text-center lg:text-left">
                <div class="text-3xl font-bold text-rose-600">4.9</div>
                <div class="text-sm text-gray-600">Rating</div>
              </div>
              <div class="text-center lg:text-left">
                <div class="text-3xl font-bold text-rose-600">3+</div>
                <div class="text-sm text-gray-600">Tahun Pengalaman</div>
              </div>
            </div>
          </div>

          <!-- Image/Visual -->
          <div
            class="relative"
            v-motion
            :initial="{ opacity: 0, x: 50 }"
            :visible="{ opacity: 1, x: 0 }"
            :duration="800"
            :delay="200"
          >
            <div class="relative aspect-square max-w-lg mx-auto">
              <!-- Placeholder Image -->
              <div
                class="absolute inset-0 bg-gradient-to-br from-rose-400 to-purple-400 rounded-3xl shadow-2xl"
              >
                <div
                  class="absolute inset-0 flex items-center justify-center text-white text-2xl font-semibold"
                >
                  Hero Image
                </div>
              </div>

              <!-- Floating Elements -->
              <div
                class="absolute -top-6 -right-6 bg-white rounded-2xl shadow-xl p-4"
                v-motion
                :initial="{ opacity: 0, scale: 0 }"
                :visible="{ opacity: 1, scale: 1 }"
                :delay="600"
              >
                <div class="flex items-center gap-3">
                  <div class="w-12 h-12 bg-rose-100 rounded-full flex items-center justify-center">
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
                    <div class="font-semibold text-gray-900">Profesional</div>
                    <div class="text-sm text-gray-600">Terapis Berpengalaman</div>
                  </div>
                </div>
              </div>

              <div
                class="absolute -bottom-6 -left-6 bg-white rounded-2xl shadow-xl p-4"
                v-motion
                :initial="{ opacity: 0, scale: 0 }"
                :visible="{ opacity: 1, scale: 1 }"
                :delay="800"
              >
                <div class="flex items-center gap-3">
                  <div
                    class="w-12 h-12 bg-purple-100 rounded-full flex items-center justify-center"
                  >
                    <svg
                      class="w-6 h-6 text-purple-600"
                      fill="none"
                      stroke="currentColor"
                      viewBox="0 0 24 24"
                    >
                      <path
                        stroke-linecap="round"
                        stroke-linejoin="round"
                        stroke-width="2"
                        d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z"
                      />
                    </svg>
                  </div>
                  <div>
                    <div class="font-semibold text-gray-900">Booking Mudah</div>
                    <div class="text-sm text-gray-600">Langsung via WhatsApp</div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Scroll Indicator -->
    <div
      class="absolute bottom-8 left-1/2 transform -translate-x-1/2"
      v-motion
      :initial="{ opacity: 0, y: -20 }"
      :visible="{ opacity: 1, y: 0 }"
      :delay="1000"
    >
      <div class="flex flex-col items-center gap-2 text-gray-600">
        <span class="text-sm">Scroll untuk melihat lebih banyak</span>
        <svg class="w-6 h-6 animate-bounce" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M19 14l-7 7m0 0l-7-7m7 7V3"
          />
        </svg>
      </div>
    </div>
  </section>
</template>

<script setup>
import BaseButton from '@/components/ui/BaseButton.vue'
</script>
