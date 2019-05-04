<template>
  <section id="welcome" class="section welcome hero is-fullheight-with-navbar">
    <div class="hero-body">
      <div class="container">
        <countdown date="March 15, 2020"></countdown>
      </div>
    </div>
  </section>
</template>

<script>
  import Countdown from '~/components/Countdown';

  export default {
    name: 'HomePage',

    components: {
      Countdown,
    },
  };
</script>

<style lang="scss" scoped>
  @import '@/assets/scss/main.scss';

  #welcome.hero {
    background-image: url("~static/main_bg@2x.jpg");
    background-position: center bottom;
    background-repeat: no-repeat;
    background-attachment: fixed;
    background-size: cover;
  }
</style>
