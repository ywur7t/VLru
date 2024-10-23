<template>
    <div class="event-card">
      <div class="event-card-content">

        <img :src="event.image" alt="Event image" class="event-image" />

        <div class="event-info">

          <div class="event-category">
            <span>{{ event.category }}</span>
            <span class="divider">·</span>
            <span>{{ event.type }}</span>
          </div>

          <h2 class="event-title">{{ event.title }}</h2>

          <p class="event-description">{{ event.description }}</p>

          <!-- <p class="event-date">{{ event.date }}</p> -->

          <div class="event-actions">
            <button class="price-button">{{ event.price }}</button>
            <button class="favorite-button" @click="toggleFavorite">
              <span v-if="isFavorite">❤️</span>
              <span v-else>🤍</span>
            </button>
          </div>

        </div>
      </div>
    </div>
  </template>

  <script>
  export default {
    props: {
      event: Object // Принимает объект события как пропс
    },
    data() {
      return {
        isFavorite: false // Для отслеживания состояния "Избранное"
      };
    },
    methods: {
      toggleFavorite() {
        this.isFavorite = !this.isFavorite; // Изменение состояния избранного
      }
    }
  };
  </script>





<style scoped>
.event-card{
  margin-bottom: 20px;
  height: inherit;
  border-radius: 4%;
  flex:1;
  overflow: hidden;

}
img{

  width:clamp(50%,50%,10%);;
  max-width: 100%;
  height: auto;
  border-radius: 10%;
  object-fit: contain;
  padding: 2%;
}

.event-card-content{
  display:flex;
  flex-direction: row;
  gap:2%;
}
.event-info{
  display: flex;
  flex-direction: column;
}
.event-category{
  display: flex;
  align-items: center;
  gap: 0.5vw;
}
.event-category span{
  color:#F97D41;
  font-family: "Wix Madefor Text", "Roboto",serif;
  font-size:1.5vw;
  font-weight:500;
  line-height: 1.5vw;
  margin-top:5%;
}


.event-title{
  font-family: "TT Autonomous Trl", "Roboto",serif;
  font-size:2.5vw;
  font-weight:500;
  line-height: 2.5vw;
  margin-bottom:0;
}

.event-description{
  font-family: "Wix Madefor Text", "Roboto",serif;
  font-size:1vw;
  font-weight:500;
  line-height: 1vw;
  color:#6C6C6D;
  width: 60%;
}

.price-button{
  background-color: #1489F0;
  color: #fff;
  padding:2%;
  border:0;
  border-radius: 12px;
  font-family: "Wix Madefor Display", "Roboto",serif;
  font-size: 1vw;
  font-weight: 300;
  line-height: 1vw;
  gap:1%;

  cursor:pointer;
}
.price-button:hover{
  background-color: #14436c;
}
.price-button:active{
  background-color: #acd3f6;
}

.favorite-button{
  background: transparent;
  cursor: pointer;
  border:0;
}
..favorite-button:active{

}

@media (max-width:375px) {
  .event-category span{
    font-size:3vw;
    line-height: 2vw;
  }
  .event-title{
    font-size:3vw;
    line-height: 3vw;
    margin-bottom:0;
  }
  .event-description {
    font-size:3vw;
    line-height: 2.5vw;
    margin-bottom:0;
  }
}

</style>
