<script setup>
    import EventCard from './EventCard.vue'



</script>


<template>

    <div class="carousel">

      <div class="carousel-slides" :style="carouselStyle">
        <EventCard v-for="(event, index) in events" :key="index" :event="event" class="carousel-slide"/>
      </div>

      <div class="carousel-controls">
        <button class="carousel-control prev" @click="prevSlide">&#10094;</button>
        <button class="carousel-control next" @click="nextSlide">&#10095;</button>
      </div>


      <div class="carousel-indicators">
        <span v-for="(slide, index) in events" :key="index" :class="{'active': index === currentIndex}" @click="goToSlide(index)"></span>
      </div>

    </div>










</template>


<script>
export default {
    components: {
      EventCard
    },
    data() {
      return {
        currentIndex: 0,
        events: [
          {
            image: "https://github.com/ywur7t/VLru/blob/main/VLRU/src/assets/4cd07b1826b5eaea63f0fe79bdb78db0.png?raw=true",
            category: "Концерт",
            type: "Живая музыка",
            title: "Магия Севера",
            description: "Волшебный концерт Олены УУТАЙ во Владивостоке 10 ноября 2024",
            date: "10 ноября 2024",
            price: "От 600 ₽"
          },
          {
            image: "https://github.com/ywur7t/VLru/blob/main/VLRU/src/assets/4cd07b1826b5eaea63f0fe79bdb78db0.png?raw=true",
            category: "Концерт",
            type: "Живая музыка",
            title: "Магия Севера",
            description: "Волшебный концерт Олены УУТАЙ во Владивостоке 10 ноября 2024",
            date: "10 ноября 2024",
            price: "От 600 ₽"
          },{
            image: "https://github.com/ywur7t/VLru/blob/main/VLRU/src/assets/4cd07b1826b5eaea63f0fe79bdb78db0.png?raw=true",
            category: "Концерт",
            type: "Живая музыка",
            title: "Магия Севера",
            description: "Волшебный концерт Олены УУТАЙ во Владивостоке 10 ноября 2024",
            date: "10 ноября 2024",
            price: "От 600 ₽"
          },
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
        this.currentIndex = (this.currentIndex + 1) % this.events.length;
      },
      prevSlide() {
        this.currentIndex =
          (this.currentIndex - 1 + this.events.length) % this.events.length;
      },
      goToSlide(index) {
        this.currentIndex = index;
      }
    }
  };
</script>


<style scoped>

    #wrapper {
      display: flex;
      position: relative;
      flex-wrap: nowrap;

      justify-content: center;
      border:  1px;
      border-color: #BEC8DB;
      border-radius:16px;
      background:#F9F9FB;
      width:100%;

      border: 1px solid #ccc;
      padding: 20px;
      margin-bottom: 20px;
      height: inherit;
      border-radius: 7%;

      overflow: hidden;
    }


    .event-navigation{
      display: flex;
      flex-direction: column;
      justify-content: space-between;
    }
    .navigation_stripes{
      display: flex;
      justify-content: space-between;
      margin-bottom: auto;
    }
    .stripe{
      background-color: #0074bc;
      width: 20px;
      height: 2px;
      margin:auto 10%;
    }
    .navigation_buttons{
      display: flex;
      justify-content: space-between;
    }









    .carousel {
      position: relative;
      width: 100%;
      height: inherit;
      overflow: hidden;

      border:  1px solid;
      border-color: #BEC8DB;
      border-radius:16px;
      background:#F9F9FB;

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
      background: #FFFFFF;
      color: black;
      border: 1px #BEC8DB solid ;
      border-radius: 12px;
      width:clamp(50px,100%,10px);
      height:auto;
      font-size: 24px;
      padding: 10px;
      cursor: pointer;
      z-index: 1;
    }
    .carousel-control:hover{
      background-color: #1489F0;
      color: white;
    }

    .carousel-control.prev {
      right: 100px;
      width: clamp(50px,100%,10px);

    }

    .carousel-control.next {
      right: 10px;
    }

    .carousel-indicators {
      position: absolute;
      bottom: 10px;
      width: 100%;
      text-align: right;
      top: 10px;
      right:10px;
      pointer-events: none;
    }

    .carousel-indicators span {
      display: inline-block;
      width: 4%;
      height: 1px;
      background-color: #333;
      margin: 0 5px;
      border-radius: 50%;
      cursor: pointer;
    }

    .carousel-indicators .active {
      background-color: #1489F0;
    }
    .carousel-controls {
      position: absolute;
      bottom: 15%;
      right: 1%;
      display: flex;
      gap: 10px;
      width:fit-content;
      font-size: 1.5vw;
    }


    @media (max-width: 375px){
      .carousel-controls{
        gap:1px;
        width:10px;
      }
      .carousel-control.prev{
        width:1vw;
        height:1vw;
        border-radius: 7px;
        font-size: 3vw;
        line-height: 0;
        padding:3vw 4vw 3vw 3vw;
      }
      .carousel-control.next{
        width:1vw;
        height:1vw;
        border-radius: 7px;
        font-size: 3vw;
        line-height: 0;
        padding:3vw 4vw 3vw 3vw;
      }


    }
</style>