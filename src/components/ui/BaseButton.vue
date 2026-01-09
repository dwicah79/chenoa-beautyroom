<template>
  <button
    :class="[
      'inline-flex items-center justify-center font-semibold transition-all duration-300',
      'focus:outline-none focus:ring-2 focus:ring-offset-2',
      variantClasses,
      sizeClasses,
      'hover:scale-105 active:scale-95',
    ]"
    v-motion
    :initial="{ opacity: 0, scale: 0.9 }"
    :visible="{ opacity: 1, scale: 1 }"
  >
    <slot />
  </button>
</template>

<script setup>
import { computed } from 'vue'

const props = defineProps({
  variant: {
    type: String,
    default: 'primary',
    validator: (value) => ['primary', 'secondary', 'outline'].includes(value),
  },
  size: {
    type: String,
    default: 'md',
    validator: (value) => ['sm', 'md', 'lg'].includes(value),
  },
})

const variantClasses = computed(() => {
  const variants = {
    primary: 'bg-rose-600 text-white hover:bg-rose-700 focus:ring-rose-500',
    secondary: 'bg-gray-800 text-white hover:bg-gray-900 focus:ring-gray-500',
    outline:
      'border-2 border-rose-600 text-rose-600 hover:bg-rose-600 hover:text-white focus:ring-rose-500',
  }
  return variants[props.variant]
})

const sizeClasses = computed(() => {
  const sizes = {
    sm: 'px-4 py-2 text-sm rounded-lg',
    md: 'px-6 py-3 text-base rounded-lg',
    lg: 'px-8 py-4 text-lg rounded-xl',
  }
  return sizes[props.size]
})
</script>
