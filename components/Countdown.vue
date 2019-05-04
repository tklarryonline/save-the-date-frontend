<template>
  <section class="has-text-centered">
    <div class="container columns">
      <div class="column">
        <h1 class="digits">{{ days }}</h1>
        <h5 class="text">Days</h5>
      </div>
      <div class="column">
        <h1 class="digits">{{ hours }}</h1>
        <h5 class="text">Hours</h5>
      </div>
      <div class="column">
        <h1 class="digits">{{ minutes }}</h1>
        <h5 class="text">Minutes</h5>
      </div>
    </div>
  </section>
</template>

<script>
  const MILLISECONDS_IN_A_MINUTE = 60000;
  const MINUTES_IN_AN_HOUR = 60;
  const HOURS_IN_A_DAY = 24;
  const MINUTES_IN_A_DAY = MINUTES_IN_AN_HOUR * HOURS_IN_A_DAY;

  const getCurrentTime = _ => (new Date()).getTime();
  const timeToMinutes = time => Math.trunc(time / MILLISECONDS_IN_A_MINUTE);
  const now = _ => timeToMinutes(getCurrentTime());

  export default {
    props: {
      date: String,
    },

    computed: {
      parsedDate() {
        return timeToMinutes(Date.parse(this.date));
      },

      timeLeft() {
        return this.parsedDate - this.now;
      },

      minutes() {
        return this.timeLeft % MINUTES_IN_AN_HOUR;
      },

      hours() {
        return Math.trunc(this.timeLeft / MINUTES_IN_AN_HOUR) % HOURS_IN_A_DAY;
      },

      days() {
        return Math.trunc(this.timeLeft / MINUTES_IN_A_DAY);
      },
    },

    data() {
      return {
        now: now(),
      };
    },

    created() {
      window.setInterval(_ => {
        this.now = now();
      }, MILLISECONDS_IN_A_MINUTE);
    },
  };
</script>

<style lang="scss" scoped>
  @import '@/assets/scss/main.scss';

  .digits,
  .text {
    @extend .has-text-white-bis;
  }

  .digits {
    @extend .subtitle, .is-1, .has-text-weight-light;
  }

  .text {
    @extend .title, .is-5;
  }
</style>
