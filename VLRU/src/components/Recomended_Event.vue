<template>
    <div class="event-card">
      <div class="event-card-content">
        <!-- Изображение события -->
        <img :src="event.image" alt="Event image" class="event-image" />

        <!-- Информация о событии -->
        <div class="event-info">
          <!-- Тип и категория события -->
          <div class="event-category">
            <span>{{ event.category }}</span>
            <span class="divider">·</span>
            <span>{{ event.type }}</span>
          </div>

          <!-- Название события -->
          <h2 class="event-title">{{ event.title }}</h2>

          <!-- Описание события -->
          <p class="event-description">{{ event.description }}</p>

          <!-- Дата события -->
          <p class="event-date">{{ event.date }}</p>

          <!-- Цена и избранное -->
          <div class="event-actions">
            <button class="price-button">{{ event.price }}</button>
            <button class="favorite-button" @click="toggleFavorite">
              <span v-if="isFavorite">❤️</span>
              <span v-else>🤍</span>
            </button>
          </div>
        </div>

        <!-- Кнопки навигации -->
        <div class="event-navigation">
          <button @click="prevEvent">❮</button>
          <button @click="nextEvent">❯</button>
        </div>
      </div>
    </div>
  </template>

  <script>
  export default {
    props:{
        image: {
            type: String,
            default: ""
        }
    },
    data() {
      return {
        isFavorite: false,
        event: {
          image: this.image,
          category: "Концерт",
          type: "Живая музыка",
          title: "Магия Севера",
          description: "Волшебный концерт Олены УУТАЙ во Владивостоке 10 ноября 2024",
          date: "10 ноября 2024",
          price: "От 600 ₽"
        }
      };
    },
    methods: {
      toggleFavorite() {
        this.isFavorite = !this.isFavorite;
      },
      prevEvent() {
        // Логика для предыдущего события
      },
      nextEvent() {
        // Логика для следующего события
      }
    }
  };
</script>
<!--
<style scoped>
  .event-card {
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: #f9f9f9;
    border-radius: 10px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    padding: 20px;
    max-width: 800px;
    margin: 20px auto;
  }

  .event-card-content {
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  .event-image {
    width: 200px;
    height: 300px;
    border-radius: 10px;
    object-fit: cover;
    margin-right: 20px;
  }

  .event-info {
    flex-grow: 1;
  }

  .event-category {
    font-size: 14px;
    color: #ff5722;
    font-weight: bold;
  }

  .divider {
    margin: 0 5px;
  }

  .event-title {
    font-size: 24px;
    margin: 10px 0;
  }

  .event-description {
    font-size: 16px;
    color: #666;
  }

  .event-date {
    margin-top: 10px;
    font-weight: bold;
  }

  .event-actions {
    display: flex;
    align-items: center;
    margin-top: 15px;
  }

  .price-button {
    background-color: #007bff;
    color: white;
    border: none;
    padding: 10px 20px;
    border-radius: 20px;
    cursor: pointer;
    margin-right: 15px;
  }

  .favorite-button {
    background: none;
    border: none;
    font-size: 20px;
    cursor: pointer;
  }

  .event-navigation {
    display: flex;
    flex-direction: column;
  }

  .event-navigation button {
    background: none;
    border: none;
    font-size: 20px;
    cursor: pointer;
    padding: 10px;
  }
</style> -->
