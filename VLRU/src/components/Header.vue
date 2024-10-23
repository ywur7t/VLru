<script setup>

    import IconVLRU from './icons/IconVLRU.vue'
    import IconLens from './icons/IconLens.vue'
    import IconFavorite from './icons/IconFavorite.vue'

    import SelectComponent from './SelectComponent.vue'
    import SearchBar from './SearchBar.vue';
    import Events_List from './Events_List.vue';


    const options = [
        { value: '0', text: 'Владивосток' },
        { value: '1', text: 'Штыково' },
        { value: '2', text: 'Арсеньев' },
        { value: '3', text: 'Находка' },
        { value: '4', text: 'Уссурийск' },
        { value: '5', text: 'Артем' }
    ]
    const events= [
        "Все события",
        "Концерты",
        "Спектакли",
        "Детям",
        "Стендап",
        "Городское событие",
        "Музеи и галереи"
    ]
</script>


<template>
    <div id="header">
      <div id="header_navigation">
          <div id="navigation_container">

            <div id="container_left">
                <a id="logo" href="https://www.vl.ru/"> <IconVLRU /> </a>

                <div id="container_city">
                  <a id="afisha" href="#"><span>Афиша</span></a>
                  <SelectComponent :options="options"
                  v-model="selectedOption" label=""/>
                </div>
            </div>

            <div id="searchbar">
            <IconLens />
                <SearchBar v-model="searchText" />
            </div>

            <div id="container_content">
                <a href="#"> <IconFavorite /> </a>
                <div id="content_buttons">
                    <button id="content_addbtn">Добавить событие</button>
                    <button id="content_loginbtn">Войти</button>
                </div>
            </div>

          </div>

          <Events_List :categories = events />
      </div>
    </div>

</template>

<style scoped>

    #header{
        position: fixed;
        top: 0;
        left: 0;
        width: 100vw;
        background-color: #fff;
        box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        z-index: 1000;
    }

    #header_navigation{
        margin: 0 10%;
    }

    #navigation_container{
        display: flex;
        justify-content: space-between;
        align-items: center;
    }

    #container_left{
        display: flex;
        align-items: center;
    }

    #container_city{
        font-family: 'TT Autonomous Trl', 'Roboto', serif;
        color:#F97D41;
        font-weight: 400;
        font-size: 1.5vw;
        line-height: 1.5vw;
        margin-left:1.5vw;
    }
    #container_city span{
        margin:auto;
    }

    #searchbar{
        display: flex;
        align-items: center;
        background: #F9F9FB;
        border-radius: 12px;
        gap: 1%;
    }

    #container_content{
        display: flex;
        align-items: center;
        justify-content: flex-end;
        gap:1vw;

    }

    #content_buttons{
        display: flex;
        gap: 1vw;
        flex:1;
        padding:1%;
    }


    #content_addbtn{
        border-radius: 12px;
        border: 1px #BEC8DB solid;
        gap: 2%;
        font-family: 'Wix Madefor Text', 'Roboto',serif;
        font-size: 1vw;
        line-height: 1vw;
        background: #fff;
        cursor: pointer;
    }
    #content_addbtn:hover{
        background: #1489F0;
        color:white;
    }
    #content_addbtn:active{
        background: #0f6fc3;
        color:white;
    }

    #content_loginbtn{
        border-radius: 12px;
        border: 1px #BEC8DB solid;
        padding: 10% 5%;
        gap: 2%;
        font-family: 'Wix Madefor Text', 'Roboto',serif;
        font-size: 1vw;
        line-height: 1vw;
        background: #fff;
        cursor: pointer;
    }
    #content_loginbtn:hover{
        background: #1489F0;
        color:white;
    }
    #content_loginbtn:active{
        background: #0f6fc3;
        color:white;
    }

    #afisha{
        text-decoration: none;
        color:#F97D41;

    }
    #afisha:hover{
        filter: brightness(1.3);
        transition: filter 0.3s ease;
    }

    @media (max-width: 375px){
        #afisha{
            font-size: 3vw;
        }

        #searchbar svg{
            width: 3vw;
            margin-right:-50px;
        }
        #logo svg{
            width:10vw;
        }
        #content_addbtn{
            display: none;
        }
        #content_loginbtn{
            font-size: 3vw;
            padding: 20%;
        }
        #navigation_container{
            justify-items: flex-end;
        }
    }

</style>