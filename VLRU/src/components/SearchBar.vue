<template>
    <div>
      <input type="text" v-model="searchQuery"
        @input="onSearch" placeholder = "Событие, концерт, спектакль" />
    </div>
  </template>

  <script>
  export default {
    props: {
      value: {
        type: String,
        default: ""
      }
    },
    data() {
      return {
        searchQuery: this.value // Привязываем к v-model
      };
    },
    methods: {
      onSearch() {
        // При изменении вводимого текста вызываем событие input
        this.$emit("input", this.searchQuery);
      }
    },
    watch: {
      value(newVal) {
        this.searchQuery = newVal; // Обновляем при изменении из родителя
      }
    }
  };
  </script>

<style scoped>
input {
  padding: 2%;
  border: 1px solid #ccc;
  border-radius: 4px;
  width: 30vw;
  font-family: 'Wix Madefor Text', 'Roboto',serif;
  font-size: 1vw;
  line-height: 1vw;
}

@media (max-width: 375px){
  input{
      display: none;
  }

}
</style>
