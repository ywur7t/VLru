<template>
    <div>
      <label for="select">{{ label }}</label>
      <select v-model="selectedValue" @change="onChange">
        <option v-for="option in options" :key="option.value" :value="option.value" >
          {{ option.text }}
        </option>
      </select>
    </div>
  </template>

<script>
  export default {
    props: {
      options: {
        type: Array,
        required: true
      },
      label: {
        type: String,
        default: "Select an option"
      },
      value: {
        type: [String, Number],
        default: ""
      }
    },
    data() {
      return {
        selectedValue: '0'
      };
    },
    methods: {
      onChange() {
        this.$emit("input", this.selectedValue);
      }
    },
    watch: {
      value(newVal) {
        this.selectedValue = newVal;
      }
    }
  };
</script>

<style scoped>

  select{
    border: none;
    font-family: 'Wix Madefor Text', 'Roboto', serif;
    font-size: 1vw;
    line-height: 1vw;
    cursor: pointer;
  }
  select:focus {
    outline: none;
    border-color: #3498db;
  }
  select:hover{
    color: #666666;
  }


  @media (max-width:375px)  {
    select{
      font-size: 2.5vw;
    }
  }


</style>