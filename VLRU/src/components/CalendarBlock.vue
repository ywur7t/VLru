<script setup>

</script>


<template>
    <div class="calendar-container">
      <div class="controls">
        <button @click="prevDate">&lt;</button>
        <span class="icon">📅</span>
        <button @click="nextDate">&gt;</button>
      </div>
      <div class="date-list">
        <div v-for="(date, index) in visibleDates" :key="index" class="date-item">
          <span>{{ date.day }}</span>
          <span>{{ date.date }}</span>
        </div>
      </div>
      <div class="filter-section">
        <button v-for="filter in filters" :key="filter" class="filter-button">
          {{ filter }}
        </button>
      </div>
    </div>
</template>



<style scoped>
    .calendar-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    background: black;
    }

    .controls {
    display: flex;
    align-items: center;
    margin-bottom: 10px;
    }

    .icon {
    margin: 0 10px;
    font-size: 24px;
    }

    .date-list {
    display: flex;
    justify-content: space-between;
    width: 100%;
    overflow-x: auto;
    margin-bottom: 10px;
    }

    .date-item {
    text-align: center;
    padding: 10px;
    }

    .filter-section {
    display: flex;
    justify-content: space-around;
    width: 100%;
    }

    .filter-button {
    padding: 5px 10px;
    background-color: #f0f0f0;
    border: 1px solid #ccc;
    border-radius: 5px;
    }
</style>
