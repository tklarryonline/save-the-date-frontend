<template>
  <section class="section">
    <countdown date="March 15, 2020"></countdown>
  </section>
</template>

<script>
import Countdown from '~/components/Countdown'

export default {
  name: 'HomePage',

  components: {
    Countdown
  }
}
</script>
