<script setup>
import { ref } from 'vue';
import IconLens from './icons/IconLens.vue'

// Get the current month and year
const currentDate = new Date();
const monthNames = [
  'Январь', 'Февраль', 'Март', 'Апрель', 'Май', 'Июнь',
  'Июль', 'Август', 'Сентябрь', 'Октябрь', 'Ноябрь', 'Декабрь'
];
const daysOfWeek = ['вс', 'пн', 'вт', 'ср', 'чт', 'пт', 'сб'];

const monthName = ref(monthNames[currentDate.getMonth()]);
const visibleDates = ref([]);
const selectedDates = ref([]);

// Generate the days for the current month
const generateDays = () => {
  const year = currentDate.getFullYear();
  const month = currentDate.getMonth();
  const daysInMonth = new Date(year, month + 1, 0).getDate();

  for (let day = 1; day <= daysInMonth; day++) {
    const date = new Date(year, month, day);
    visibleDates.value.push({
      day: daysOfWeek[date.getDay()],
      date: day.toString(),
      fullDate: date
    });
  }
};

generateDays();

const scrollContainer = ref(null);

const scrollLeft = () => {
  if (scrollContainer.value) {
    scrollContainer.value.scrollBy({ left: -100, behavior: 'smooth' });
  }
};

const scrollRight = () => {
  if (scrollContainer.value) {
    scrollContainer.value.scrollBy({ left: 100, behavior: 'smooth' });
  }
};

const selectDate = (date) => {
  if (selectedDates.value.length === 0 || selectedDates.value.length === 2) {
    selectedDates.value = [date];
  } else {
    selectedDates.value.push(date);
    if (selectedDates.value[0] > selectedDates.value[1]) {
      selectedDates.value.reverse();
    }
  }
};

const isSelected = (date) => {
  if (selectedDates.value.length === 1) {
    return selectedDates.value[0].getTime() === date.getTime();
  } else if (selectedDates.value.length === 2) {
    return date >= selectedDates.value[0] && date <= selectedDates.value[1];
  }
  return false;
};
</script>
<script>
export default {
  data() {
    return {
      buttons: [
        { label: 'Поиск', class: 'search-button' },
        { label: 'Бесплатно', class: 'free-button' },
        { label: 'Детям', class: 'child-button' },

        {
          label: 'Пушкинская карта',
          class: 'pushkin-button',
          icon: 'https://s3-alpha-sig.figma.com/img/7d5e/a11e/e8306d074636fb8665b0b43917511ae5?Expires=1730678400&Key-Pair-Id=APKAQ4GOSFWCVNEHN3O4&Signature=FJKfYcIQI4kA9CUsaoAL2rvztn7-eaBKFhyk84KuVkKAsXqK3fgFDGis6GLT4whPaty63sPlIcTYneGdikl2EKcHmsjV3jpYwyCskcHPo~Lrgl~hRw7wjyrQMd3J~7TKJoi9Ogv3d4H0Y0dPoF4OJtDr19NpmUG7dQuHnxynomQP80aFWPl9sq3JLv5uD~iQwuMyvI9OB9ghenlAfF6-pSxcn2E1JWFVcK0zjrUqiTzhiDekfN6Y~sxr9Sa9HfUbwWFb-E6QGLT~hpQO15BDmpgSegH8sWaSj4X9O6u9W-yAm4ugkpLfH2ckG9ng7d6aBX1KTuJwI4QE0xFBZQJhbQ__'
        },

      ],

      priceRanges: [
        { label: '0 - 1000 ₽', value: '0-1000' },
        { label: '1001 - 5000 ₽', value: '1001-5000' },
        { label: '5001 - 10000 ₽', value: '5001-10000' },
        { label: 'больше 10000 ₽', value: '10000-1000000' }
      ],
      selectedPriceRange: '',
      showPriceDropdown: false,
      price: 0
    };
  },
  methods: {
    handleClick(label) {
      console.log('Нажата кнопка:', label);
    },
    togglePriceDropdown() {
      this.showPriceDropdown = !this.showPriceDropdown;
    }
  }
};
</script>
<template>
  <div class="calendar-container">
    <span class="month-name">{{ monthName }}</span>
    <div class="scroll-button left" @click="scrollLeft"></div>
    <div class="scroll-container" ref="scrollContainer">
      <div class="wrapper">
        <div
          v-for="(date, index) in visibleDates"
          :key="index"
          class="day-wrapper"
          :class="{ selected: isSelected(date.fullDate) }"
          @click="selectDate(date.fullDate)"
        >
          <div class="day">
            <div class="day-inner">
              <div class="date-text">{{ date.date }}</div>
              <div class="name">{{ date.day }}</div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="scroll-button right" @click="scrollRight"></div>
  </div>






  <div class="calendar_navigation">



    <button v-for="(button, index) in buttons" :key="index"
      :class="button.class" @click="handleClick(button.label)">

      <img v-if="button.icon" :src="button.icon" :alt="button.label" class="icon" />

      {{ button.label }}
    </button>

    <select v-model="selectedPriceRange" @change="handlePriceChange" class="price-select">
      <option value="" disabled selected>Цена</option>
      <option v-for="range in priceRanges" :key="range.label" :value="range.value">
        {{ range.label }}
      </option>
    </select>

    <div v-if="showPriceDropdown" class="price-dropdown">
      <label for="priceRange">Выберите диапазон цены:</label>
      <input type="range" id="priceRange" v-model="price" min="0" max="10000" />
      <span>{{ price }} ₽</span>
    </div>



  </div>


</template>

<style scoped>
.calendar-container {
  font-family: "YS Text", Arial, "Helvetica Neue", Helvetica, sans-serif;
  position: relative;
  padding-right: 30px;
}

.month-name {
  font-family: 'TT Autonomous Trl', 'Roboto', serif;
  font-size: 1.5vw;
  margin-bottom: 10px;
}

.scroll-container {
  overflow-x: auto;
  white-space: nowrap;
  scrollbar-width: none;

}

.scroll-container::-webkit-scrollbar {
  display: none;
}

.wrapper {
  display: flex;
  flex-wrap: nowrap;
  width:50%;
  font-family: "Wix Madefor Text", 'Roboto', serif;
  font-size: 2vw;

}

.day-wrapper {
  flex: 0 0 auto;
  width: 15%;
  box-sizing: border-box;
  padding: 5px;
  cursor: pointer;
}

.day {
  background: #fff;
  border: 1px solid #ccc;
  border-radius: 5px;
  text-align: center;
  padding: 1%;
}

.day-inner {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.name {
  font-size: 0.9em;
  color: #666;
}

.scroll-button {
  width: 23px;
  height: 100%;
  display: flex;
  background: #fff;
  position: absolute;
  top: 0;
  bottom: 0;
  align-items: center;
  cursor: pointer;
}

.scroll-button.left {
  left: -30px;
  box-shadow: 1px 0 0 0 #fff, -1px 0 0 0 #fff;
}

.scroll-button.right {
  right: -30px;
  box-shadow: 1px 0 0 0 #fff, -1px 0 0 0 #fff;
}

.scroll-button::after {
  content: "";
  width: 12px;
  height: 22px;
  display: block;
  background: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTMiIGhlaWdodD0iMjIiIGZpbGw9Im5vbmUiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyI+PHBhdGggb3BhY2l0eT0iLjgiIGQ9Ik0xIDIxbDEwLTEwTDEgMSIgc3Ryb2tlPSIjMDAwIiBzdHJva2Utd2lkdGg9IjIiIHN0cm9rZS1saW5lY2FwPSJyb3VuZCIvPjwvc3ZnPg==) 0 0 / 12px 22px no-repeat;
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
}

.scroll-button.left::after {
  transform: translateY(-50%) rotate(180deg);
}

.day-wrapper.selected .day {
  background: #339AF0;
}
.lens{
  width:50px;
}
button{
  border: 1px #D4D4D4 solid;
  border-radius: 12px;
  background: #FFFFFF;
  font-family: 'Wix Madefor Text', 'Roboto',serif;
  font-size:1vw;
  line-height: 2vw;
  margin-right:1%;
  cursor: pointer;
}
button:hover{
  background: #1489F0;
  color: white;
}
img.icon{
  width:20%;
  height:auto;
  bottom: 0;
  left: 0;
  position: absolute;

}
.pushkin-button{
  position: relative;
  width:15%;
  display: flex;
  padding-left:2%;
}
.calendar_navigation{
  display: flex;
  margin-top: 20px;
  flex-direction: row;
}
.price-button {
position: relative;
}
.price-dropdown {
  position: absolute; /* Абсолютное позиционирование для наложения */
  top: 100%; /* Размещаем под кнопкой */
  left: 0; /* По левому краю кнопки */
  margin-top: 5px; /* Отступ от кнопки */
  border: 1px solid #ccc;
  padding: 10px;
  background-color: #f9f9f9;
  z-index: 1000; /* Обеспечиваем, чтобы выпадающее меню было над другими элементами */
  font-family: 'Wix Madefor Text', 'Roboto',serif;
  font-size:1vw;
  line-height: 2vw;
}
.price-select {
  font-family: 'Wix Madefor Text', 'Roboto',serif;
  font-size:1vw;
  line-height: 2vw;
  cursor: pointer;
  border: 0;
  width:6%;
}

@media (max-width:375px) {
  .month-name{
    font-size:3vw;
  }
  .day{
    font-size:3vw;
  }
  .calendar_navigation button{
    font-size:2.5vw;
  }
  .pushkin-button{
    width:fit-content;
  }
  .scroll-button.right{
    display: none;
  }
}

</style>
