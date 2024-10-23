<template>
    <div class="event-card">
        <div class="event_tags">

            <div class="tags">
                <span class="tag concert">Концерт</span>
                <span class="tag age">16+</span>
                <span class="tag p">P</span>
            </div>



        </div>

        <img :src="imageSrc" alt="Концерт" class="event-image" />

        <div class="price">
            <span class="price price">от 6000 P</span>
            <span class="fav" v-if="isFavorite">❤️</span>
            <span class="fav" v-else>🤍</span>
        </div>

    <div class="event-details">
        <h2>Магия Севера Волшебный</h2>
        <p>10 ноября, 19:00</p>
        <p>Андерграунд</p>
    </div>
    </div>
</template>

<script>
  export default {
    data() {
      return {


        imageSrc: "https://s3-alpha-sig.figma.com/img/0a64/94df/4cd07b1826b5eaea63f0fe79bdb78db0?Expires=1730678400&Key-Pair-Id=APKAQ4GOSFWCVNEHN3O4&Signature=kwQAPr-Fv2j~holPtnGI3rMCAsDqzVfS4qVgN4pKIkevydDQ~QZRkGIqGk1dCvpuHVqktJ5Fz7vewLqcwxwV1tL6KNjhNxdzstDw~CYk-j3GKLeMk0X0gNa7plJDaWpXlKFFnZtvTX~B3cwvSFZKRjZPZlgETcOr8kBWlCepyi0doRz1WDyhGc1fEcqRlEmMMDigUjIamQl45p-LJ3puX6NhxK6BjNJEj9PdWmvKK5cwCTfVVU4lgw3vvw7D7riXrnCPpEajhTSxupht9bw5GrQGH1hbLoxXF59ZHSjY6ZJVhuOG4HANQB5AzRnGtwBdpwvbtGrCH5et4~CkmeLKkw__",
        isFavorite: false // Состояние для сердечка
      };
    },
    methods: {
      toggleFavorite() {
        this.isFavorite = !this.isFavorite;
      }
    }
  };
</script>

<style scoped>
    .event-card {
        position: relative;
        width: 25%;
        border: 1px solid #ccc;
        border-radius: 10px;
        overflow: hidden;
        box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);

        font-family: 'Wix Madefor Display','Roboto',serif;
    }

    img{
        width: 100%;
        height: auto;
        margin-top:-50px;
    }

    .tags{
        display: block;
        position: relative;
        font-size:1vw;
        line-height: 1.5vw;
        padding:5%;
        height:inherit;

    }
    .price{
        display: block;
        position: relative;

        font-size:1vw;
    }
    .tag.concert{
        position: absolute;
        background: #1489F0;
        color: white;
        border-radius: 10px;
        left:0;
        padding:2%;
    }
    .tag.age{
        position: absolute;
        border-radius: 10px;
        background: #fff;
        color: #000;
        left:30%;
        padding:2%;
    }
    .tag.p{
        position: absolute;
        border-radius: 10px;
        background: #fff;
        color: #000;
        left:50%;
        padding:2%;
    }

    .price span{
        position: absolute;
        bottom:0;
        right:0;
        color:#000000;
        border-radius: 12px;
        background: white;
    }
    .price.price{
        right:10%;
    }
    .price .fav{

        right:0;

    }

    .event-details h2{
        margin:0 0 5% 0;
        font-size:60%;
        line-height: 1.5vw;
        font-family: 'TT Autonomous Trl', 'Roboto',serif;
    }
    .event-details p{
        margin:0;
        padding:0;
        font-size:1vw;
        color:#6C6C6D;
        line-height:1.5vw;
        font-family: 'Wix Madefor Text', 'Roboto',serif;
    }

    @media (max-width:375px) {
        .event-card{
            width:75vw;
            display: flex;

        }
        img{
            display: inline;
            margin:0;
            width:40%;
        }
        .tags{
            display: none;
        }
        .event-details h2{
            font-size:3vw;
            text-wrap: wrap;
            line-height: 3vw;
        }
        .event-details p{
            font-size:3vw;
            text-wrap: wrap;
            line-height: 3vw;
        }

    }
  </style>
