<script setup>
    import RecomendBlock from './RecomendBlock.vue';
    import RecomendEmail from './RecomendEmail.vue';
    import CalendarBlock1 from './CalendarBlock1.vue';
    import EventComponent from './EventComponent.vue';

</script>

<template>
    <div id="content">

        <div id="content_recomendations">
            <RecomendBlock />
            <RecomendEmail />
        </div>
        <div class="afisha">
            <div id="city-afisha">
                <span>Афиша Владивостока</span>
                <button v-html="buttonText"></button>
            </div>

            <div id="content_calendar">
                <CalendarBlock1 />
            </div>

            <div class="Events_city">
                <EventComponent />
                <EventComponent />
                <EventComponent />
                <EventComponent />
            </div>

            <div id="city-afisha">
                <span>Концерты</span>
                <button v-html="buttonText"></button>
            </div>

            <div class="Events_city">
                <EventComponent />
                <EventComponent />
                <EventComponent />
                <EventComponent />
            </div>

            <div id="city-afisha">
                <span>События</span>
                <button v-html="buttonText"></button>
            </div>

            <div class="Events_city">
                <EventComponent />
                <EventComponent />
                <EventComponent />
                <EventComponent />
            </div>

        </div>
    </div>
</template>
<script>
export default {
  data() {
    return {
      buttonText: "Все &#10095;"
    };
  },
  mounted() {
    this.updateButtonText();
    window.addEventListener('resize', this.updateButtonText);
  },
  beforeUnmount() {
    window.removeEventListener('resize', this.updateButtonText);
  },
  methods: {
    updateButtonText() {
      if (window.innerWidth < 375) {
        this.buttonText = "&#10095;";
      } else {
        this.buttonText = "Все &#10095;";
      }
    }
  }
};
</script>


<style scoped>

    #content{
        display: flex;
        flex-direction: column;
        align-items: center;
        height: 100vh;
        padding: 15vh 10vw;
    }
    #content_recomendations{
        display: flex;
        justify-content: space-evenly;
        margin: 0 ;
        min-height:40vh;
        width:auto;
        overflow: hidden;
        gap: 5%;

    }
    .afisha{
        align-self: flex-start;
        margin: 5% 0;
        width:80vw;


        font-family: 'TT Autonomous Trl', 'Roboto', serif;
        font-size:2.5vw;
        line-height: 3vw;

    }
    #city-afisha{
        display: flex;
        gap:1%;
        flex-direction: row;
        margin: 0;
    }

    .afisha button{
        border: 1px #D4D4D4 solid;
        border-radius: 12px;
        font-family: 'Wix Madefor Text', 'Roboto', serif;
        font-size:1vw;
        line-height: 1vw;
        background: white;
        cursor: pointer;
    }
    .afisha button:hover{
        background: #1489F0;
        color: white;
    }
    .afisha button:active{
        background: #0b4f8b;
        color: white;
    }
    .Events_city{
        display: flex;
        flex-direction: row;
        margin: 5% 0;
        gap: 10%;
        width:80vw;
        overflow: auto;

    }

    @media (max-width: 375px){
        #content{
            padding: 20% 0;
        }

        #content_recomendations{
            flex-direction: column;
            margin:0;
        }
        #city-afisha{
            width:100%;
        }
        #city-afisha span{
            font-size:5vw;
            text-wrap: nowrap;
        }
        #city-afisha button{
            font-size:3vw;
            padding:5%;
        }
        .Events_city{
            flex-direction: column;
        }
    }

</style>