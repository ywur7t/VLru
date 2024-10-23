<script setup>
    import RecomendBlock from './RecomendBlock.vue';
    import RecomendEmail from './RecomendEmail.vue';
    import CalendarBlock from './CalendarBlock.vue';
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
                <button>Все &#10095;</button>
            </div>

            <div id="content_calendar">
                <CalendarBlock />
            </div>
        </div>
    </div>
</template>

<style scoped>

    #content{
        display: flex;
        flex-direction: column;
        align-items: center;
        height: 100vh;
        padding: 15vh 17vw;
    }
    #content_recomendations{
        display: flex;
        justify-content: space-evenly;
        margin: 0 20%;
        overflow: hidden;
        gap: 5%;

    }
    .afisha{
        align-self: flex-start;
        margin: 5% 0;
        width:50vw;


        font-family: 'TT Autonomous Trl', 'Roboto', serif;
        font-size:2.5vw;
        line-height: 3vw;

    }
    #city-afisha{
        display: flex;
        gap:5%;
        flex-direction: row;
        margin: 0 0 5% 0;
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

    @media (max-width: 375px){
        #content{
            padding: 20% 0;
        }

        #content_recomendations{
            flex-direction: column;
            margin:0;
        }
    }

</style>