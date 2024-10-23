<template>
    <div class="carousel">
      <!-- Стрелка "Назад" -->
      <button class="carousel-control prev" @click="prevSlide">
        &#10094;
      </button>

      <!-- Слайды -->
      <div class="carousel-slides" :style="carouselStyle">
        <div v-for="(slide, index) in slides" :key="index" class="carousel-slide">
          <img :src="slide" alt="Slide" />
        </div>
      </div>

      <!-- Стрелка "Вперед" -->
      <button class="carousel-control next" @click="nextSlide">
        &#10095;
      </button>

      <!-- Индикаторы (точки) -->
      <div class="carousel-indicators">
        <span
          v-for="(slide, index) in slides"
          :key="index"
          :class="{'active': index === currentIndex}"
          @click="goToSlide(index)"
        ></span>
      </div>
    </div>
  </template>

  <script>
  export default {
    data() {
      return {
        currentIndex: 0,
        slides: [
          'https://via.placeholder.com/800x300?text=Slide+1',
          'https://via.placeholder.com/800x300?text=Slide+2',
          'https://via.placeholder.com/800x300?text=Slide+3',
        ]
      };
    },
    computed: {
      // Вычисляем стиль для смещения слайдов
      carouselStyle() {
        return {
          transform: `translateX(-${this.currentIndex * 100}%)`
        };
      }
    },
    methods: {
      nextSlide() {
        this.currentIndex = (this.currentIndex + 1) % this.slides.length;
      },
      prevSlide() {
        this.currentIndex =
          (this.currentIndex - 1 + this.slides.length) % this.slides.length;
      },
      goToSlide(index) {
        this.currentIndex = index;
      }
    }
  };
  </script>

  <style scoped>
  .carousel {
    position: relative;
    width: 800px;
    height: 300px;
    overflow: hidden;
  }

  .carousel-slides {
    display: flex;
    transition: transform 0.5s ease;
  }

  .carousel-slide {
    min-width: 100%;
  }

  .carousel-slide img {
    width: 100%;
    height: auto;
  }

  .carousel-control {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    background: rgba(0, 0, 0, 0.5);
    color: white;
    border: none;
    font-size: 24px;
    padding: 10px;
    cursor: pointer;
    z-index: 1;
  }

  .carousel-control.prev {
    left: 10px;
  }

  .carousel-control.next {
    right: 10px;
  }

  .carousel-indicators {
    position: absolute;
    bottom: 10px;
    width: 100%;
    text-align: center;
  }

  .carousel-indicators span {
    display: inline-block;
    width: 10px;
    height: 10px;
    background-color: #ccc;
    margin: 0 5px;
    border-radius: 50%;
    cursor: pointer;
  }

  .carousel-indicators .active {
    background-color: #333;
  }
  </style>
