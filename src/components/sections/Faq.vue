```vue
<script setup>
import { ref } from "vue";
import { Plus, Minus } from "lucide-vue-next";

const activeFaq = ref(null);

const toggleFaq = (index) => {
  activeFaq.value = activeFaq.value === index ? null : index;
};

const faqs = [
  {
    question: "Berapa lama proses pembuatan website?",
    answer:
      "Waktu pengerjaan bervariasi tergantung kebutuhan. Umumnya website company profile selesai dalam 3–7 hari kerja.",
  },
  {
    question: "Apakah website sudah responsif di semua perangkat?",
    answer:
      "Ya, seluruh website yang kami buat sudah mobile-friendly dan dapat diakses dengan baik di smartphone, tablet, maupun desktop.",
  },
  {
    question: "Apakah saya mendapatkan domain dan hosting?",
    answer:
      "Tidak. Kami tidak menyediakan paket lengkap termasuk domain dan hosting.",
  },
  {
    question: "Apakah website bisa diubah atau dikembangkan di kemudian hari?",
    answer:
      "Tentu. Website dibuat dengan struktur yang mudah dikembangkan sehingga dapat ditambah fitur sesuai kebutuhan bisnis Anda.",
  },
];
</script>

<template>
  <section id="faq" class="py-24 bg-slate-50">
    <div class="max-w-7xl mx-auto px-6">
      <!-- Heading -->
      <div class="text-center mb-16">
        <span
          class="inline-block px-4 py-2 rounded-full bg-blue-100 text-blue-600 text-sm font-medium"
        >
          FAQ
        </span>

        <h2 class="mt-4 text-4xl font-bold text-gray-900">
          Pertanyaan yang Sering Ditanyakan
        </h2>

        <p class="mt-4 text-gray-600 max-w-2xl mx-auto">
          Temukan jawaban dari pertanyaan yang paling sering diajukan oleh calon
          klien kami.
        </p>
      </div>

      <!-- Content -->
      <div class="grid lg:grid-cols-2 gap-16 items-center">
        <!-- Illustration -->
        <div class="hidden lg:flex justify-center">
          <img
            src="/images/faq.webp"
            alt="FAQ Illustration"
            class="w-full max-w-md floating"
          />
        </div>

        <!-- FAQ -->
        <div class="space-y-4">
          <div
            v-for="(faq, index) in faqs"
            :key="index"
            class="bg-white rounded-2xl border border-gray-100 shadow-sm hover:shadow-md transition"
          >
            <button
              @click="toggleFaq(index)"
              class="w-full flex items-center justify-between p-6 text-left"
            >
              <span class="font-semibold text-gray-900">
                {{ faq.question }}
              </span>

              <div
                class="w-8 h-8 rounded-full bg-blue-50 flex items-center justify-center"
              >
                <Minus
                  v-if="activeFaq === index"
                  class="w-4 h-4 text-blue-600"
                />

                <Plus v-else class="w-4 h-4 text-blue-600" />
              </div>
            </button>

            <div
              class="overflow-hidden transition-all duration-300"
              :class="
                activeFaq === index
                  ? 'max-h-40 opacity-100'
                  : 'max-h-0 opacity-0'
              "
            >
              <div class="px-6 pb-6 text-gray-600 leading-relaxed">
                {{ faq.answer }}
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
