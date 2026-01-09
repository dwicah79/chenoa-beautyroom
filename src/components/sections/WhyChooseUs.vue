<template>
  <section id="why-choose" class="py-20 bg-white">
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
          Mengapa Memilih Kami
        </div>
        <h2 class="text-3xl md:text-4xl font-bold text-gray-900 mb-4">
          Alasan Kenapa Harus Chenoa Beauty Room
        </h2>
        <p class="text-lg text-gray-600 max-w-2xl mx-auto">
          Kami berkomitmen memberikan pengalaman terbaik untuk setiap klien
        </p>
      </div>

      <!-- Reasons Grid -->
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8">
        <div
          v-for="(reason, index) in reasons"
          :key="reason.title"
          class="text-center group"
          v-motion
          :initial="{ opacity: 0, y: 30 }"
          :visible="{ opacity: 1, y: 0 }"
          :delay="index * 100"
        >
          <div
            class="w-20 h-20 bg-gradient-to-br from-rose-500 to-purple-500 rounded-2xl flex items-center justify-center mx-auto mb-6 group-hover:scale-110 transition-transform duration-300 shadow-lg"
          >
            <div v-html="reason.icon" class="text-white"></div>
          </div>
          <h3 class="text-xl font-bold text-gray-900 mb-3">{{ reason.title }}</h3>
          <p class="text-gray-600">{{ reason.description }}</p>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const reasons = [
  {
    title: 'Profesional & Berpengalaman',
    description: 'Tim terapis tersertifikasi dengan pengalaman lebih dari 3 tahun',
    icon: `<svg class="w-10 h-10" fill="none" stroke="currentColor" viewBox="0 0 24 24">
      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4M7.835 4.697a3.42 3.42 0 001.946-.806 3.42 3.42 0 014.438 0 3.42 3.42 0 001.946.806 3.42 3.42 0 013.138 3.138 3.42 3.42 0 00.806 1.946 3.42 3.42 0 010 4.438 3.42 3.42 0 00-.806 1.946 3.42 3.42 0 01-3.138 3.138 3.42 3.42 0 00-1.946.806 3.42 3.42 0 01-4.438 0 3.42 3.42 0 00-1.946-.806 3.42 3.42 0 01-3.138-3.138 3.42 3.42 0 00-.806-1.946 3.42 3.42 0 010-4.438 3.42 3.42 0 00.806-1.946 3.42 3.42 0 013.138-3.138z"/>
    </svg>`,
  },
  {
    title: 'Produk Premium',
    description: 'Menggunakan produk berkualitas tinggi dan aman untuk kulit',
    icon: `<svg class="w-10 h-10" fill="none" stroke="currentColor" viewBox="0 0 24 24">
      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 3v4M3 5h4M6 17v4m-2-2h4m5-16l2.286 6.857L21 12l-5.714 2.143L13 21l-2.286-6.857L5 12l5.714-2.143L13 3z"/>
    </svg>`,
  },
  {
    title: 'Hasil Memuaskan',
    description: 'Garansi kepuasan dengan hasil natural dan tahan lama',
    icon: `<svg class="w-10 h-10" fill="none" stroke="currentColor" viewBox="0 0 24 24">
      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M14 10h4.764a2 2 0 011.789 2.894l-3.5 7A2 2 0 0115.263 21h-4.017c-.163 0-.326-.02-.485-.06L7 20m7-10V5a2 2 0 00-2-2h-.095c-.5 0-.905.405-.905.905 0 .714-.211 1.412-.608 2.006L7 11v9m7-10h-2M7 20H5a2 2 0 01-2-2v-6a2 2 0 012-2h2.5"/>
    </svg>`,
  },
  {
    title: 'Harga Terjangkau',
    description: 'Kualitas premium dengan harga yang bersahabat di kantong',
    icon: `<svg class="w-10 h-10" fill="none" stroke="currentColor" viewBox="0 0 24 24">
      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8c-1.657 0-3 .895-3 2s1.343 2 3 2 3 .895 3 2-1.343 2-3 2m0-8c1.11 0 2.08.402 2.599 1M12 8V7m0 1v8m0 0v1m0-1c-1.11 0-2.08-.402-2.599-1M21 12a9 9 0 11-18 0 9 9 0 0118 0z"/>
    </svg>`,
  },
]
</script>
