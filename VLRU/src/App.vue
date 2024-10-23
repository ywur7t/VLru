<script setup>

  import Header from './components/Header.vue';
  import MainContent from './components/MainContent.vue';



</script>

<template>

  <Header />
  <MainContent />

</template>




<style scoped>

  #form_post{
    background-color: #1489F0;
  }

  #content_email{
    background-image: url('./assets/email_background.png');
    background-repeat: no-repeat;
  }

  #men{
    width: 60px;
    height: auto;
  }

  header {
    line-height: 1.5;
  }

  .logo {
    display: block;
    margin: 0 auto 2rem;
  }

  @media (min-width: 1024px) {
    header {
      display: flex;
      place-items: center;
      padding-right: calc(var(--section-gap) / 2);
    }

    .logo {
      margin: 0 2rem 0 0;
    }

    header .wrapper {
      display: flex;
      place-items: flex-start;
      flex-wrap: wrap;
    }
  }
</style>
