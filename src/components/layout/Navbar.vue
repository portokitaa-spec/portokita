<script setup>
import { ref, onMounted, onBeforeUnmount } from "vue";

const mobileMenu = ref(false);
const isScrolled = ref(false);

const handleScroll = () => {
  isScrolled.value = window.scrollY > 50;
};

onMounted(() => {
  window.addEventListener("scroll", handleScroll);
});

onBeforeUnmount(() => {
  window.removeEventListener("scroll", handleScroll);
});
</script>

<template>
  <nav class="w-full navbar" :class="{ 'navbar-scrolled': isScrolled }">
    <div class="max-w-7xl mx-auto px-4">
      <!-- Navbar -->
      <div class="flex items-center justify-between h-16">
        <!-- Logo - Left -->
        <div class="flex-shrink-0">
          <img
            src="/images/logo.webp"
            alt="Company Logo"
            class="w-12 h-12 object-contain transition-all duration-300 rounded-2xl"
            :class="{ 'logo-scrolled': isScrolled }"
          />
        </div>

        <!-- Menu Desktop - Center -->
        <div class="hidden md:flex items-center justify-center flex-1">
          <ul class="flex items-center gap-10">
            <li>
              <a
                href="#home"
                class="nav-link"
                :class="{ 'nav-link-scrolled': isScrolled }"
                >Beranda</a
              >
            </li>
            <li>
              <a
                href="#about"
                class="nav-link"
                :class="{ 'nav-link-scrolled': isScrolled }"
                >Tentang</a
              >
            </li>
            <li>
              <a
                href="#price"
                class="nav-link"
                :class="{ 'nav-link-scrolled': isScrolled }"
                >Harga</a
              >
            </li>
            <li>
              <a
                href="#workflow"
                class="nav-link"
                :class="{ 'nav-link-scrolled': isScrolled }"
                >Alur Kerja</a
              >
            </li>
            <li>
              <a
                href="#faq"
                class="nav-link"
                :class="{ 'nav-link-scrolled': isScrolled }"
                >FAQ</a
              >
            </li>
            <li>
              <a
                href="#"
                class="nav-link"
                :class="{ 'nav-link-scrolled': isScrolled }"
              ></a>
            </li>
          </ul>
        </div>

        <!-- CTA Button - Right -->
        <div class="hidden md:block flex-shrink-0">
          <a
            href="#"
            class="px-5 py-2.5 bg-blue-600 text-white rounded-lg font-medium hover:bg-blue-700 transition duration-300 shadow-md btn-cta"
            :class="{ 'btn-cta-scrolled': isScrolled }"
          >
            Hubungi Kami
          </a>
        </div>

        <!-- Hamburger - Right (Mobile) -->
        <button
          class="md:hidden hamburger-btn flex-shrink-0"
          :class="{ 'hamburger-scrolled': isScrolled }"
          @click="mobileMenu = !mobileMenu"
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            class="w-7 h-7 transition-colors duration-300"
            :class="{ 'text-gray-700': isScrolled, 'text-white': !isScrolled }"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M4 6h16M4 12h16M4 18h16"
            />
          </svg>
        </button>
      </div>

      <!-- Mobile Menu -->
      <transition name="fade">
        <div
          v-if="mobileMenu"
          class="md:hidden mt-2 bg-white/95 backdrop-blur-xl rounded-xl shadow-2xl overflow-hidden mobile-menu"
          :class="{ 'mobile-menu-scrolled': isScrolled }"
        >
          <ul class="flex flex-col p-4 gap-4">
            <li>
              <a href="#" class="nav-link-mobile"> Beranda </a>
            </li>

            <li>
              <a href="#" class="nav-link-mobile"> Tentang </a>
            </li>

            <li>
              <a href="#" class="nav-link-mobile"> Harga </a>
            </li>

            <li>
              <a href="#" class="nav-link-mobile"> Alur Kerja </a>
            </li>

            <li>
              <a href="#" class="nav-link-mobile"> FAQ </a>
            </li>

            <li>
              <a href="#" class="nav-link-mobile"> </a>
            </li>

            <li>
              <a
                href="#"
                class="block text-center px-5 py-3 bg-blue-600 text-white rounded-lg font-medium hover:bg-blue-700 transition"
              >
                Hubungi Kami
              </a>
            </li>
          </ul>
        </div>
      </transition>
    </div>
  </nav>
</template>

<style scoped>
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  z-index: 99999;
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
  backdrop-filter: blur(10px);
  background: rgba(255, 255, 255, 0.014);
  border-bottom: 1px solid rgba(255, 255, 255, 0.05);
}

.navbar-scrolled {
  background: rgba(255, 255, 255, 0.95);
  backdrop-filter: blur(12px);
  box-shadow: 0 4px 30px rgba(0, 0, 0, 0.08);
  border-bottom: 1px solid rgba(0, 0, 0, 0.05);
  padding: 2px 0;
}

.nav-link {
  position: relative;
  color: #ffffff;
  font-weight: 600;
  transition: color 0.3s ease;
  text-decoration: none;
  font-size: 0.95rem;
  letter-spacing: 0.3px;
}

.nav-link-scrolled {
  color: #374151;
}

.nav-link:hover {
  color: #30d6ff;
}

.nav-link-scrolled:hover {
  color: #2563eb;
}

.nav-link::after {
  content: "";
  position: absolute;
  left: 0;
  bottom: -6px;
  width: 0;
  height: 2.5px;
  background: linear-gradient(90deg, #30d6ff, #3b82f6);
  transition: width 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  border-radius: 2px;
}

.nav-link-scrolled::after {
  background: linear-gradient(90deg, #3b82f6, #8b5cf6);
}

.nav-link:hover::after {
  width: 100%;
}

.btn-cta {
  background: #3b82f6;
  color: #fff;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  text-decoration: none;
}

.btn-cta-scrolled {
  background: #3b82f6;
  box-shadow: 0 4px 15px rgba(59, 130, 246, 0.3);
}

.btn-cta:hover {
  background: #2563eb;
  transform: translateY(-2px);
  box-shadow: 0 8px 25px rgba(59, 130, 246, 0.4);
}

.btn-cta:active {
  transform: translateY(0);
}

.hamburger-btn {
  background: transparent;
  border: none;
  cursor: pointer;
  padding: 4px;
  border-radius: 8px;
  transition: all 0.3s ease;
}

.hamburger-btn:hover {
  background: rgba(255, 255, 255, 0.1);
}

.hamburger-scrolled:hover {
  background: rgba(0, 0, 0, 0.05);
}

.mobile-menu {
  background: rgba(255, 255, 255, 0.95);
  backdrop-filter: blur(12px);
  box-shadow: 0 10px 40px rgba(0, 0, 0, 0.1);
}

.mobile-menu-scrolled {
  background: rgba(255, 255, 255, 0.98);
  box-shadow: 0 10px 40px rgba(0, 0, 0, 0.15);
}

.nav-link-mobile {
  display: block;
  color: #374151;
  font-weight: 500;
  padding: 8px 12px;
  border-radius: 8px;
  transition: all 0.2s ease;
  text-decoration: none;
}

.nav-link-mobile:hover {
  color: #2563eb;
  background: rgba(59, 130, 246, 0.08);
}

.fade-enter-active,
.fade-leave-active {
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
  transform: translateY(-10px) scale(0.98);
}

@media (max-width: 1024px) {
  .nav-link {
    font-size: 0.9rem;
  }

  .nav-link-scrolled {
    font-size: 0.9rem;
  }
}

@media (max-width: 768px) {
  .navbar {
    padding: 3px 0;
  }

  .navbar-scrolled {
    padding: 2px 0;
  }
}
</style>
