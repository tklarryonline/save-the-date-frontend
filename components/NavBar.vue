<template>
  <nav class="navbar is-fixed-top container" role="navigation" aria-label="main navigation">
    <div class="navbar-brand">
    </div>
    <div class="navbar-menu">
      <div class="navbar-end">
        <nuxt-link
          class="navbar-item"
          v-for="(item, key) of items"
          :key="key"
          :to="item.to"
          exact-active-class="is-active"
        >
          {{ item.title }}
        </nuxt-link>
      </div>
    </div>
  </nav>
</template>

<script>
  export default {
    data() {
      return {
        items: [
          {
            title: 'Home',
            to: {
              name: 'index',
            },
          },
          {
            title: 'Details',
            to: {
              name: 'detail',
            },
          },
          {
            title: 'Story',
            to: {
              name: 'story',
            },
          },
        ],
      };
    },
  };
</script>
