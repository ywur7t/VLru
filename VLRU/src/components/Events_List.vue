<template>
    <div class="category-list">
      <ul>
        <li
          v-for="(category, index) in categories"
          :key="index"
          :class="{ active: activeCategory === category }"
          @click="setActiveCategory(category)"
        >
          {{ category }}
        </li>
      </ul>
    </div>
</template>

<script>
  export default {
    props: {
        categories: {
        type: [String],
        default: ""
      }
    },
    data() {
      return {
        activeCategory: "Все события",
        events: this.categories
      };
    },
    methods: {
      setActiveCategory(category) {
        this.activeCategory = category;
      }
    }
  };
</script>

<style scoped>
    .category-list {
        display: flex;
        align-items: center;
        overflow-x: auto;
        white-space: nowrap;
        font-family: 'Wix Madefor Text', 'Roboto',serif;
        font-size: 1vw;
    }

    ul {
        list-style: none;
        padding: 0;
        margin: 0;
        display: flex;
    }

    li {
        padding: 2% 3%;
        cursor: pointer;
    }

    li:last-child {
        border-right: none;
    }

    li.active {

    }

    li:hover {
        color: #666666;
    }

    @media (max-width: 375px){
       .category-list {
            font-size: 3vw;
        }
    }
</style>
