```vue
<template>
  <section id="price" class="relative py-24 bg-slate-50 overflow-hidden">
    <img
      src="/public/images/pattern1.png"
      alt=""
      class="absolute top-6 left-0 w-90 opacity-20 -z-0 rotate-30"
    />
    <img
      src="/public/images/pattern2.png"
      alt=""
      class="absolute bottom-0 right-0 w-90 opacity-20 -z-0"
    />

    <div class="relative z-10 max-w-7xl mx-auto px-6">
      <!-- Heading -->
      <div class="text-center mb-16">
        <span
          class="inline-block px-4 py-2 rounded-full bg-blue-100 text-blue-600 text-sm font-medium"
        >
          Paket Website
        </span>

        <h2 class="mt-4 text-4xl font-bold text-gray-900">
          Pilih Paket yang Sesuai dengan Kebutuhan Anda
        </h2>

        <p class="mt-4 text-gray-600 max-w-2xl mx-auto">
          Website profesional dengan desain modern, responsif, dan performa
          optimal untuk membantu bisnis Anda berkembang di era digital.
        </p>
      </div>

      <!-- Cards -->
      <div class="grid md:grid-cols-2 xl:grid-cols-4 gap-8">
        <!-- Company Profile -->
        <div
          class="bg-white rounded-3xl p-8 border border-gray-100 shadow-sm hover:shadow-xl hover:-translate-y-2 transition-all duration-300"
        >
          <div
            class="w-14 h-14 rounded-2xl bg-blue-50 flex items-center justify-center mb-6"
          >
            <Globe class="w-7 h-7 text-blue-600" />
          </div>

          <h3 class="text-xl font-bold text-gray-900">Company Profile</h3>

          <p class="text-gray-500 text-sm mt-2">
            Website profesional untuk memperkenalkan bisnis dan meningkatkan
            kredibilitas perusahaan.
          </p>

          <div class="mt-6">
            <span class="text-sm text-gray-500">Mulai dari</span>

            <h4 class="text-3xl font-bold text-blue-600 mt-1">Rp 100 Rb</h4>
          </div>

          <ul class="mt-6 space-y-3 text-sm text-gray-600">
            <li class="flex items-center gap-2">
              <Check class="w-4 h-4 text-green-500" />
              Hingga 3 Halaman atau lebih sesuai kebutuhan
            </li>

            <li class="flex items-center gap-2">
              <Check class="w-4 h-4 text-green-500" />
              Responsive Design
            </li>
          </ul>

          <button
            class="w-full mt-8 py-3 rounded-xl bg-blue-600 text-white font-medium hover:bg-blue-700 transition"
          >
            Konsultasi
          </button>
        </div>

        <!-- Landing Page -->
        <div
          class="relative bg-white rounded-3xl p-8 border-2 border-blue-600 shadow-lg hover:-translate-y-2 transition-all duration-300"
        >
          <span
            class="absolute -top-3 right-6 bg-blue-600 text-white text-xs px-3 py-1 rounded-full"
          >
            Terpopuler
          </span>

          <div
            class="w-14 h-14 rounded-2xl bg-blue-50 flex items-center justify-center mb-6"
          >
            <Rocket class="w-7 h-7 text-blue-600" />
          </div>

          <h3 class="text-xl font-bold text-gray-900">Portofolio</h3>

          <p class="text-gray-500 text-sm mt-2">
            Digunakan untuk persoal branding baik untuk melamar kerja, ataupun
            yang lain
          </p>

          <div class="mt-6">
            <span class="text-sm text-gray-500">Mulai dari</span>

            <h4 class="text-3xl font-bold text-blue-600 mt-1">Rp 60 Rb</h4>
          </div>

          <ul class="mt-6 space-y-3 text-sm text-gray-600">
            <li class="flex items-center gap-2">
              <Check class="w-4 h-4 text-green-500" />
              1 Halaman Penuh
            </li>

            <li class="flex items-center gap-2">
              <Check class="w-4 h-4 text-green-500" />
              Custom Sesuai Keinginan
            </li>

            <li class="flex items-center gap-2">
              <Check class="w-4 h-4 text-green-500" />
              Responsive Design
            </li>
          </ul>

          <button
            class="w-full mt-8 py-3 rounded-xl bg-blue-600 text-white font-medium hover:bg-blue-700 transition"
          >
            Konsultasi
          </button>
        </div>

        <!-- Toko Online -->
        <div
          class="bg-white rounded-3xl p-8 border border-gray-100 shadow-sm hover:shadow-xl hover:-translate-y-2 transition-all duration-300"
        >
          <div
            class="w-14 h-14 rounded-2xl bg-blue-50 flex items-center justify-center mb-6"
          >
            <ShoppingCart class="w-7 h-7 text-blue-600" />
          </div>

          <h3 class="text-xl font-bold text-gray-900">Web UMKM</h3>

          <p class="text-gray-500 text-sm mt-2">
            Solusi e-commerce modern untuk menjual produk secara online.
          </p>

          <div class="mt-6">
            <span class="text-sm text-gray-500">Mulai dari</span>

            <h4 class="text-3xl font-bold text-blue-600 mt-1">Rp 280 Rb</h4>
          </div>

          <ul class="mt-6 space-y-3 text-sm text-gray-600">
            <li class="flex items-center gap-2">
              <Check class="w-4 h-4 text-green-500" />
              Halaman Utama
            </li>

            <li class="flex items-center gap-2">
              <Check class="w-4 h-4 text-green-500" />
              Responsive Design
            </li>

            <li class="flex items-center gap-2">
              <Check class="w-4 h-4 text-green-500" />
              Dashboard Admin
            </li>
          </ul>

          <button
            class="w-full mt-8 py-3 rounded-xl bg-blue-600 text-white font-medium hover:bg-blue-700 transition"
          >
            Konsultasi
          </button>
        </div>

        <!-- Web Custom -->
        <div
          class="bg-white rounded-3xl p-8 border border-gray-100 shadow-sm hover:shadow-xl hover:-translate-y-2 transition-all duration-300"
        >
          <div
            class="w-14 h-14 rounded-2xl bg-blue-50 flex items-center justify-center mb-6"
          >
            <Settings class="w-7 h-7 text-blue-600" />
          </div>

          <h3 class="text-xl font-bold text-gray-900">Web Custom</h3>

          <p class="text-gray-500 text-sm mt-2">
            Sistem website yang dirancang khusus sesuai kebutuhan bisnis Anda.
          </p>

          <div class="mt-6">
            <span class="text-sm text-gray-500">Mulai dari</span>

            <h4 class="text-3xl font-bold text-blue-600 mt-1">Custom</h4>
          </div>

          <ul class="mt-6 space-y-3 text-sm text-gray-600">
            <li class="flex items-center gap-2">
              <Check class="w-4 h-4 text-green-500" />
              Halaman Utama + Resonsive Design
            </li>

            <li class="flex items-center gap-2">
              <Check class="w-4 h-4 text-green-500" />
              Dashboard Admin
            </li>

            <li class="flex items-center gap-2">
              <Check class="w-4 h-4 text-green-500" />
              Optimasi Kecepatan
            </li>
          </ul>

          <button
            class="w-full mt-8 py-3 rounded-xl bg-blue-600 text-white font-medium hover:bg-blue-700 transition"
          >
            Konsultasi
          </button>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { Globe, Rocket, ShoppingCart, Settings, Check } from "lucide-vue-next";
</script>
