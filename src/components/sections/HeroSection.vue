<template>
  <section id="home" class="services-section">
    <div class="carousel" ref="carousel">
      <div class="list" ref="list">
        <div
          v-for="(service, index) in services"
          :key="index"
          class="item"
          :style="{ backgroundImage: `url(${service.image})` }"
        >
          <div class="content">
            <div class="label">Layanan</div>
            <div class="name">{{ service.title }}</div>
            <div class="des">{{ service.description }}</div>
            <div class="btn">
              <button class="btn-primary" @click="handleCta(service)">
                Coba Sekarang
              </button>
            </div>
          </div>
        </div>
      </div>

      <!-- Prev / Next arrows -->
      <div class="arrows">
        <button
          class="arrow-btn"
          @click="showSlider('prev')"
          aria-label="Previous"
        >
          <svg width="20" height="20" viewBox="0 0 20 20" fill="none">
            <path
              d="M13 4L7 10L13 16"
              stroke="currentColor"
              stroke-width="2.2"
              stroke-linecap="round"
              stroke-linejoin="round"
            />
          </svg>
        </button>
        <button class="arrow-btn" @click="showSlider('next')" aria-label="Next">
          <svg width="20" height="20" viewBox="0 0 20 20" fill="none">
            <path
              d="M7 4L13 10L7 16"
              stroke="currentColor"
              stroke-width="2.2"
              stroke-linecap="round"
              stroke-linejoin="round"
            />
          </svg>
        </button>
      </div>

      <!-- Progress bar -->
      <div class="time-running" ref="timeRunning"></div>
    </div>
  </section>
</template>

<script>
export default {
  name: "ServicesCarousel",
  data() {
    return {
      timeRunning: 3000,
      timeAutoNext: 5000,
      runTimeOut: null,
      runNextAuto: null,
      isTransitioning: false,
      services: [
        {
          title: "Company Profile",
          description:
          "Website profesional untuk memperkenalkan bisnis dan membangun kredibilitas di mata pelanggan.",
          image:
          "/images/slide1.webp",
        },
        {
          title: "Portokita.id",
          description:
            "Kami membantu umkm, personal brand, dan perusahaan memiliki website modern dan siap meningkatkan kredibilitas bisnis di era digital.",
          image:
            "/images/hero.webp",
        },
        {
          title: "Website Portofolio",
          description:
            "Website portfolio untuk freelancer, kreator, dan profesional agar tampil lebih meyakinkan.",
          image:
            "/images/slide3.webp",
        },
        {
          title: "Website UMKM",
          description:
            "Membantu UMKM memiliki website profesional untuk memperluas jangkauan pemasaran digital.",
          image:
            "/public/images/slide4.webp",
        },
        {
          title: "Website Redesign",
          description:
            "Mengubah tampilan website lama menjadi lebih modern, responsif, dan profesional.",
          image:
            "/public/images/slide5.webp",
        },
      ],
    };
  },
  mounted() {
    this.resetTimeAnimation();
    this.startAutoPlay();
  },
  beforeDestroy() {
    this.cleanup();
  },
  methods: {
    showSlider(type) {
      if (this.isTransitioning) return;
      this.isTransitioning = true;

      const carousel = this.$refs.carousel;
      const list = carousel.querySelector(".list");
      const sliderItems = list.querySelectorAll(".item");

      if (type === "next") {
        list.appendChild(sliderItems[0]);
        carousel.classList.add("next");
      } else {
        list.prepend(sliderItems[sliderItems.length - 1]);
        carousel.classList.add("prev");
      }

      clearTimeout(this.runTimeOut);
      this.runTimeOut = setTimeout(() => {
        carousel.classList.remove("next", "prev");
        this.isTransitioning = false;
      }, this.timeRunning);

      this.restartAutoPlay();
    },

    restartAutoPlay() {
      clearTimeout(this.runNextAuto);
      this.resetTimeAnimation();
      this.startAutoPlay();
    },

    resetTimeAnimation() {
      const runningTime = this.$refs.timeRunning;
      if (runningTime) {
        runningTime.style.animation = "none";
        void runningTime.offsetHeight;
        runningTime.style.animation = `runningTime ${this.timeAutoNext / 1000}s linear 1 forwards`;
      }
    },

    startAutoPlay() {
      this.runNextAuto = setTimeout(() => {
        this.showSlider("next");
      }, this.timeAutoNext);
    },

    cleanup() {
      clearTimeout(this.runTimeOut);
      clearTimeout(this.runNextAuto);
    },

    handleCta(service) {
      console.log("CTA clicked for:", service.title);
    },
  },
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700;800;900&display=swap");

*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

/* ─── Section wrapper ─── */
.services-section {
  width: 100%;
  background: #050814;
}

/* ─── Carousel ─── */
.carousel {
  width: 100%;
  height: 100vh;
  min-height: 560px;
  max-height: 900px;
  overflow: hidden;
  position: relative;
}

/* ─── Items — base (thumbnail) state ─── */
.carousel .list .item {
  width: 160px;
  height: 220px;
  position: absolute;
  top: 82%;
  transform: translateY(-70%);
  left: 68%;
  border-radius: 16px;
  box-shadow: 0 20px 50px rgba(0, 0, 0, 0.4);
  background-position: center;
  background-size: cover;
  z-index: 100;
  transition: all 0.8s cubic-bezier(0.4, 0, 0.2, 1);
  cursor: pointer;
}

/* ─── First two items: fullscreen hero ─── */
.carousel .list .item:nth-child(1),
.carousel .list .item:nth-child(2) {
  top: 0;
  left: 0;
  transform: none;
  border-radius: 0;
  width: 100%;
  height: 100%;
  cursor: default;
}

/* ─── Thumbnail stagger positions ─── */
.carousel .list .item:nth-child(3) {
  left: 68%;
  transition-delay: 0.1s;
}
.carousel .list .item:nth-child(4) {
  left: calc(68% + 176px);
  transition-delay: 0.15s;
}
.carousel .list .item:nth-child(5) {
  left: calc(68% + 352px);
  transition-delay: 0.2s;
}
.carousel .list .item:nth-child(6) {
  left: calc(68% + 528px);
  transition-delay: 0.25s;
}
.carousel .list .item:nth-child(n + 7) {
  left: calc(68% + 704px);
  opacity: 0;
  transition-delay: 0s;
}

/* ─── Gradient overlay on hero items ─── */
.carousel .list .item:nth-child(1)::after,
.carousel .list .item:nth-child(2)::after {
  content: "";
  position: absolute;
  inset: 0;
  background: linear-gradient(
    110deg,
    rgba(5, 8, 20, 0.82) 0%,
    rgba(5, 8, 20, 0.48) 50%,
    rgba(5, 8, 20, 0.1) 100%
  );
}

/* ─── Content (only shown on 2nd item = active hero) ─── */
.list .item .content {
  position: absolute;
  top: 50%;
  left: clamp(40px, 8vw, 120px);
  transform: translateY(-50%);
  width: min(520px, 86vw);
  color: #fff;
  z-index: 10;
  display: none;
}

.list .item:nth-child(2) .content {
  display: block;
}

/* ─── Content text animations ─── */
.content .label {
  font-size: 14px;
  font-weight: 700;
  letter-spacing: 4px;
  color: #ffffff;
  background-color: #7f81fd2f;
  padding: 8px;
  width: 140px;
  align-items: center;
  justify-content: center;
  display: flex;
  border-radius: 30px;
  margin-bottom: 14px;
  opacity: 0;
  animation: animate 0.8s ease-in-out 0.2s 1 forwards;
}

.content .name {
  font-size: clamp(36px, 6vw, 72px);
  font-weight: 600;
  line-height: 1.05;
  text-shadow: 0 4px 24px rgba(0, 0, 0, 0.5);
  margin-bottom: 16px;
  opacity: 0;
  animation: animate 0.8s ease-in-out 0.5s 1 forwards;
}

.content .des {
  font-size: clamp(14px, 1.6vw, 17px);
  font-weight: 400;
  line-height: 1.7;
  color: rgba(255, 255, 255, 0.72);
  margin-bottom: 28px;
  text-shadow: 1px 2px 8px rgba(0, 0, 0, 0.4);
  opacity: 0;
  animation: animate 0.8s ease-in-out 0.8s 1 forwards;
}

.content .btn {
  opacity: 0;
  animation: animate 0.8s ease-in-out 1.1s 1 forwards;
}

.content .btn button {
  padding: 13px 30px;
  border: none;
  cursor: pointer;
  font-size: 15px;
  font-weight: 600;
  border-radius: 10px;
  transition:
    background 0.25s ease,
    transform 0.2s ease,
    box-shadow 0.25s ease;
}

.content .btn .btn-primary {
  background: #3b82f6;
  color: #fff;
}
.content .btn .btn-primary:hover {
  background: #2563eb;
  transform: translateY(-2px);
  box-shadow: 0 12px 30px rgba(59, 130, 246, 0.4);
}
.content .btn .btn-primary:active {
  transform: translateY(0);
}

/* ─── Slide-in animation for content ─── */
@keyframes animate {
  from {
    opacity: 0;
    transform: translateY(60px);
    filter: blur(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
    filter: blur(0);
  }
}

/* ─── Arrows ─── */
.arrows {
  position: absolute;
  bottom: 32px;
  right: clamp(20px, 5vw, 60px);
  display: flex;
  gap: 10px;
  z-index: 200;
}

.arrow-btn {
  width: 44px;
  height: 44px;
  border-radius: 50%;
  border: 1.5px solid rgba(255, 255, 255, 0.22);
  background: rgba(255, 255, 255, 0.08);
  color: #fff;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  backdrop-filter: blur(10px);
  transition:
    background 0.2s ease,
    border-color 0.2s ease,
    transform 0.15s ease;
}

.arrow-btn:hover {
  background: rgba(59, 130, 246, 0.55);
  border-color: #3b82f6;
  transform: scale(1.08);
}

.arrow-btn:active {
  transform: scale(0.95);
}

/* ─── Progress bar ─── */
.carousel .time-running {
  position: absolute;
  z-index: 1000;
  width: 0%;
  height: 3px;
  background: linear-gradient(90deg, #3b82f6, #93c5fd);
  left: 0;
  top: 0;
  box-shadow: 0 0 16px rgba(59, 130, 246, 0.5);
}

@keyframes runningTime {
  from {
    width: 0%;
  }
  to {
    width: 100%;
  }
}

/* ─── next/prev transition classes ─── */
.carousel.next .list .item:nth-child(1) {
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  transform: none;
  border-radius: 0;
}

.carousel.prev .list .item:nth-child(2) {
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  transform: none;
  border-radius: 0;
}

/* ════════════════════════════════════════
   RESPONSIVE
════════════════════════════════════════ */

/* ── Tablet (≤ 900px) ── */
@media (max-width: 900px) {
  .carousel .list .item {
    width: 130px;
    height: 180px;
  }

  .carousel .list .item:nth-child(3) {
    left: 65%;
  }
  .carousel .list .item:nth-child(4) {
    left: calc(65% + 146px);
  }
  .carousel .list .item:nth-child(5) {
    left: calc(65% + 292px);
  }
  .carousel .list .item:nth-child(6) {
    left: calc(65% + 438px);
  }
  .carousel .list .item:nth-child(n + 7) {
    left: calc(65% + 584px);
  }
}

/* ── Mobile landscape & small tablet (≤ 680px) ── */
@media (max-width: 680px) {
  .carousel {
    height: 100svh;
    min-height: 500px;
    max-height: none;
  }

  /* Content: anchor to bottom */
  .list .item .content {
    bottom: 180px;
    left: 0;
    right: 0;
    width: 100%;
    padding: 0 24px;
  }

  /* Overlay: gradient from bottom for mobile readability */
  .carousel .list .item:nth-child(1)::after,
  .carousel .list .item:nth-child(2)::after {
    background: linear-gradient(
      to top,
      rgba(5, 8, 20, 0.9) 0%,
      rgba(5, 8, 20, 0.45) 55%,
      rgba(5, 8, 20, 0.05) 100%
    );
  }

  /* Thumbnails: smaller, 3 visible */
  .carousel .list .item {
    width: 100px;
    height: 138px;
    border-radius: 12px;
    top: 28%;
  }

  .carousel .list .item:nth-child(3) {
    left: 56%;
  }
  .carousel .list .item:nth-child(4) {
    left: calc(56% + 112px);
  }
  .carousel .list .item:nth-child(5) {
    left: calc(56% + 224px);
  }
  .carousel .list .item:nth-child(6) {
    left: calc(56% + 336px);
    opacity: 0;
  }
  .carousel .list .item:nth-child(n + 7) {
    left: calc(56% + 448px);
    opacity: 0;
  }

  /* Arrows: bottom-left on mobile */
  .arrows {
    bottom: 150px;
    right: auto;
    left: 24px;
    gap: 8px;
  }

  .arrow-btn {
    width: 40px;
    height: 40px;
  }
}

/* ── Mobile portrait (≤ 480px) ── */
@media (max-width: 480px) {
  .carousel .list .item {
    width: 84px;
    height: 116px;
    border-radius: 10px;
  }

  .carousel .list .item:nth-child(3) {
    left: 52%;
  }
  .carousel .list .item:nth-child(4) {
    left: calc(52% + 96px);
  }
  .carousel .list .item:nth-child(5) {
    left: calc(52% + 192px);
    opacity: 0;
  }
  .carousel .list .item:nth-child(6) {
    left: calc(52% + 288px);
    opacity: 0;
  }
  .carousel .list .item:nth-child(n + 7) {
    left: calc(52% + 384px);
    opacity: 0;
  }

  .content .name {
    font-size: 50px;
  }

  .content .des {
    font-size: 18px;
    padding-top: -30rem;
  }

  .content .btn button {
    padding: 10px 22px;
    font-size: 13px;
  }
}

/* ── Very small (≤ 380px) ── */
@media (max-width: 380px) {
  .carousel .list .item {
    width: 72px;
    height: 100px;
    border-radius: 8px;
  }

  .carousel .list .item:nth-child(3) {
    left: 50%;
  }
  .carousel .list .item:nth-child(4) {
    left: calc(50% + 82px);
  }
  .carousel .list .item:nth-child(5) {
    left: calc(50% + 164px);
    opacity: 0;
  }
  .carousel .list .item:nth-child(6) {
    opacity: 0;
  }

  .content .name {
    font-size: 24px;
  }

  .content .des {
    font-size: 12px;
    margin-bottom: 18px;
  }

  .list .item .content {
    bottom: 70px;
    padding: 0 18px;
  }
}

/* ── Reduced motion ── */
@media (prefers-reduced-motion: reduce) {
  .carousel .list .item {
    transition: none;
  }
  .content .label,
  .content .name,
  .content .des,
  .content .btn {
    animation: none;
    opacity: 1;
    transform: none;
  }
}
</style>
