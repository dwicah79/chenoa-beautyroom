<template>
  <div
    class="bg-white rounded-2xl shadow-soft overflow-hidden hover:shadow-soft-lg transition-all duration-300 group border border-rose-100"
    v-motion
    :initial="{ opacity: 0, y: 30 }"
    :visible="{ opacity: 1, y: 0 }"
    :delay="delay"
  >
    <!-- Icon -->
    <div class="bg-rose-500 p-8 text-white">
      <div
        class="w-16 h-16 bg-white/20 backdrop-blur-sm rounded-2xl flex items-center justify-center mb-4 group-hover:scale-110 transition-transform duration-300"
        v-html="service.icon"
      ></div>
      <h3 class="text-2xl font-bold mb-2">{{ service.title }}</h3>
      <p class="text-rose-100">{{ service.price }}</p>
    </div>

    <!-- Content -->
    <div class="p-6">
      <p class="text-slate-600 mb-6">{{ service.description }}</p>

      <!-- Features -->
      <ul class="space-y-3 mb-6">
        <li
          v-for="(feature, index) in service.features"
          :key="index"
          class="flex items-center gap-2 text-slate-700"
        >
          <svg
            class="w-5 h-5 text-rose-500 shrink-0"
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
          <span>{{ feature }}</span>
        </li>
      </ul>

      <!-- Button -->
      <BookingButton :service-name="service.title" variant="outline" size="md" class="w-full" />
    </div>
  </div>
</template>

<script setup>
import BookingButton from './BookingButton.vue'

defineProps({
  service: {
    type: Object,
    required: true,
  },
  delay: {
    type: Number,
    default: 0,
  },
})
</script>
