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
    background-position: center bottom;
    background-repeat: no-repeat;
    background-attachment: fixed;
    background-size: cover;

    @include touch {
      background-image: url("~static/main_bg@0,5x.jpg");
    }

    @media screen and (max-width: 1920px) {
      background-image: url("~static/main_bg@1x.jpg");
    }

    @media screen and (min-width: 1921px) {
      background-image: url("~static/main_bg@2x.jpg");
    }
  }
</style>
