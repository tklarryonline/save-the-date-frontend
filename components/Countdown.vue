<template>
  <section class="has-text-centered">
    <div class="container columns">
      <div class="column">
        <h1 class="subtitle is-1 has-text-weight-light digits">{{ days }}</h1>
        <h5 class="title is-5 text">Days</h5>
      </div>
      <div class="column">
        <h1 class="subtitle is-1 has-text-weight-light digits">{{ hours }}</h1>
        <h5 class="title is-5 text">Hours</h5>
      </div>
      <div class="column">
        <h1 class="subtitle is-1 has-text-weight-light digits">{{ minutes }}</h1>
        <h5 class="title is-5 text">Minutes</h5>
      </div>
      <div class="column">
        <h1 class="subtitle is-1 has-text-weight-light digits">{{ seconds }}</h1>
        <h5 class="title is-5 text">Seconds</h5>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  props: {
    date: String
  },

  computed: {
    parsedDate() {
      return timeToSeconds(Date.parse(this.date));
    },

    timeLeft() {
      return this.parsedDate - this.now
    },

    seconds() {
        return this.timeLeft % 60;
    },

    minutes() {
        return Math.trunc(this.timeLeft / 60) % 60;
    },

    hours() {
        return Math.trunc(this.timeLeft / 60 / 60) % 24;
    },

    days() {
        return Math.trunc(this.timeLeft / 60 / 60 / 24);
    }
  },

  data() {
    return {
      now: now()
    }
  },

  created() {
    window.setInterval(_ => {
      this.now = now();
    }, 1000);
  },
};

const getCurrentTime = _ => (new Date()).getTime();
const timeToSeconds = time => Math.trunc(time / 1000);
const now = _ => timeToSeconds(getCurrentTime());

</script>
