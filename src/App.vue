<script setup>
import Navbar from './components/layout/Navbar.vue'
import About from './components/sections/About.vue';
import Faq from './components/sections/Faq.vue';
import HeroSection  from './components/sections/HeroSection.vue';
import Services from './components/sections/Services.vue';
import Workflow from './components/sections/Workflow.vue';
import Footer from './components/layout/Footer.vue'

</script>

<template>
  <Navbar />
  <HeroSection />
  <About /> 
  <Services />
  <Workflow />
  <Faq />
  <Footer />
</template>
