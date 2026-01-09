<script setup>
import { RouterView } from 'vue-router'
import Navbar from './components/layout/Navbar.vue'
import Footer from './components/layout/Footer.vue'
import WhatsAppButton from './components/ui/WhatsAppButton.vue'
</script>

<template>
  <div class="min-h-screen bg-white font-sans antialiased">
    <Navbar />
    <main>
      <RouterView />
    </main>
    <Footer />
    <WhatsAppButton />
  </div>
</template>
