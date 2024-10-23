<script setup>
import IconSend from './icons/IconSend.vue'
</script>

<template>
    <div id="wrapper">

        <span>Вся Афиша в&nbsp;1&nbsp;письме</span>
        <img src="../assets/men.png">
        <form>
            <input type="text" v-model="searchQuery" placeholder="Ваш Email">
            <button @click="filterMovies"><IconSend /></button>
        </form>
    </div>
</template>


<style scoped>

    #wrapper{
        background-image: url("https://s3-alpha-sig.figma.com/img/febc/d544/03b3458a1da5e91e31db085b4e789e0c?Expires=1730678400&Key-Pair-Id=APKAQ4GOSFWCVNEHN3O4&Signature=c1kgojB4qM~fb-lWQtXzScretlmdFKiTuHnPrZHUCI5YI7zI9SP~uNpe7JOED75zw-xEUubW~dBWQooebH4jKYH4j-VJT~72KecoChZVx~7YIqc2aRPXubEAVIOOLWB3jGPXP03YBJlV8kC-tgsY6KT~4y3UJEzLF280CdsAugRnt-FpCWoi8FsLNvRQodEDUdapbcUkg3PHz6aNx7D1T3JL2T3SBXEwC8KpL~pJhpwx7gmZARKqpadk5QPMEOqhDK8lz7sOmrdVWQWbhkee18Lju79nVNahgLOot-YNma6XpfO7RlWroWfuxIDXKKKyTLKHO2oh6qy2GywofL6sTA__");
        background-repeat: no-repeat ;
        background-size: cover;
        width: 40%;
        height: 100%;
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
        gap:10px;
        font-family: 'Wix Madefor Text', 'Roboto', serif;
        font-size: 14px;
        line-height: 17.64px;

        height:30px;
    }
    button{
        background: #1489F0;
        border-radius: 12px;
        width:20%;

    }
    form{
        display: flex;
        gap:10px;
        position: absolute;

        bottom:2%;
        left:2%;

        width:100%;
    }
    img{
        position: relative;
        display: block;
        width:70%;
        height:auto;
        margin: 0 auto;
    }
</style>