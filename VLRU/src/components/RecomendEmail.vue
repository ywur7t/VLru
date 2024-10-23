<script setup>
import IconSend from './icons/IconSend.vue'
</script>

<template>
    <div id="wrapper">

        <span>Вся Афиша в&nbsp;1&nbsp;письме</span>
        <img class="men" src="https://github.com/ywur7t/VLru/blob/main/VLRU/src/assets/men.png?raw=true">
        <form>
            <input type="text" v-model="searchQuery" placeholder="Ваш Email">
            <button @click="filterMovies"><IconSend /></button>
        </form>
    </div>
</template>


<style scoped>

    #wrapper{
        background-image: url("https://github.com/ywur7t/VLru/blob/main/VLRU/src/assets/03b3458a1da5e91e31db085b4e789e0c.jpeg?raw=true");
        background-repeat: no-repeat ;
        background-size: cover;
        width: 40%;
        height: inherit;
        border-radius: 16px;
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        text-align: center;
        position: relative;
        overflow: hidden;

    }

    span{
        font-family: 'TT Autonomous Trl', 'Roboto', serif;
        font-size: clamp(8px, 2vw, 2vw);
        line-height: 28.75px;
        color:white;
        text-align: center;
        margin-bottom: auto;

    }
    input{
        border-radius: 12px;
        padding: 0.5vw 1vw;
        margin: 0 1% 0 4%;
        font-family: 'Wix Madefor Text', 'Roboto', serif;
        font-size: 14px;
        line-height: 17.64px;
        width:60%;

        height:30px;
    }
    button{
        background: #1489F0;
        border-radius: 12px;
        width:20%;
        cursor:pointer;
    }

    form{
        display: flex;

        position: absolute;

        bottom:2%;

        width:100%;
        max-width: 500px;
    }
    img{
        position: relative;
        display: block;
        width:70%;
        height:auto;
        margin: 0 auto;
    }

@media (max-width: 375px) {

    #wrapper{
        width: 100%;
        height: auto;
        display: block;
        position: relative;
    }
    .men{
        display: none;
    }
    form{
        position: relative;
        width:100%;
        padding-bottom: 3vw;
    }
    input{
        width:inherit;
        margin: 0 5vw;
    }
    button{
        margin-right:5vw;
    }
    span{
        font-size: 5vw;
        display: block;
        margin: 3vw;
    }

}


</style>