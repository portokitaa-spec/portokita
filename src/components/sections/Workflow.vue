<template>
  <section id="workflow" class="py-24 bg-white">
    <div class="max-w-7xl mx-auto px-6 text-center">

      <!-- Badge -->
      <span class="inline-flex items-center gap-1.5 px-4 py-1.5 rounded-full bg-blue-50 text-blue-700 text-sm font-medium">
        Alur Kerja
      </span>

      <!-- Heading -->
      <h2 class="mt-4 text-4xl font-bold text-gray-900">
        Proses pengerjaan yang <span class="text-blue-600">mudah</span> dan 
        <span class="text-blue-600">transparan</span>
      </h2>

      <p class="mt-4 text-gray-500 max-w-xl mx-auto leading-relaxed">
        Kami memastikan setiap proyek berjalan terstruktur sehingga
        hasil yang didapat sesuai dengan kebutuhan bisnis Anda.
      </p>

      <!-- Steps -->
      <div class="relative mt-20">

        <!-- Dashed connector line -->
        <div class="hidden lg:block absolute top-10 left-[12.5%] right-[12.5%] h-px border-t border-dashed border-gray-300 z-0" />

        <div class="grid md:grid-cols-2 lg:grid-cols-4 gap-10">
          <div
            v-for="step in steps"
            :key="step.number"
            class="relative z-10 flex flex-col items-center"
          >
            <!-- Number ring -->
            <div class="w-20 h-20 rounded-full border border-gray-200 bg-white flex items-center justify-center mb-6 shadow-sm">
              <div class="w-12 h-12 rounded-full bg-blue-600 text-white flex items-center justify-center font-semibold text-lg">
                {{ step.number }}
              </div>
            </div>

            <!-- Icon -->
            <component :is="step.icon" class="w-7 h-7 text-blue-600 mb-4" stroke-width="1.6" />

            <!-- Text -->
            <h3 class="text-lg font-bold text-gray-900 mb-2">
              {{ step.title }}
            </h3>
            <p class="text-sm text-gray-500 leading-relaxed">
              {{ step.description }}
            </p>

            <!-- Duration pill -->
            <span class="mt-4 inline-block px-3 py-1 rounded-full bg-blue-50 text-blue-700 text-xs font-medium">
              {{ step.duration }}
            </span>
          </div>
        </div>

      </div>
    </div>
  </section>
</template>

<script setup>
import { MessageSquare, LayoutDashboard, Code2, Rocket } from 'lucide-vue-next'

const steps = [
  {
    number: 1,
    title: 'Konsultasi',
    description: 'Diskusi kebutuhan website, tujuan bisnis, dan fitur yang ingin dibuat.',
    duration: '~1–2 hari',
    icon: MessageSquare,
  },
  {
    number: 2,
    title: 'Perencanaan',
    description: 'Menyusun struktur website, desain, dan alur pengerjaan sesuai kebutuhan.',
    duration: '~3–5 hari',
    icon: LayoutDashboard,
  },
  {
    number: 3,
    title: 'Development',
    description: 'Website dikembangkan dengan teknologi modern, responsif, dan optimal.',
    duration: '~7–14 hari',
    icon: Code2,
  },
  {
    number: 4,
    title: 'Launching',
    description: 'Website diuji, dipublikasikan, dan siap mendukung bisnis Anda.',
    duration: '~1–2 hari',
    icon: Rocket,
  },
]
</script>