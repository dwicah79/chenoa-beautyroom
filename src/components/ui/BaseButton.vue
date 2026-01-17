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
    primary: 'bg-rose-500 text-white hover:bg-rose-600 focus:ring-rose-200 shadow-soft',
    secondary: 'bg-slate-800 text-white hover:bg-slate-900 focus:ring-slate-300 shadow-soft',
    outline: 'border-2 border-rose-500 text-rose-500 hover:bg-rose-50 focus:ring-rose-200 bg-white',
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
