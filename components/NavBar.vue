<template>
  <nav class="navbar is-fixed-top container" role="navigation" aria-label="main navigation">
    <div class="navbar-brand">
      <nuxt-link class="navbar-item brand" to="{ name: 'index' }">Luan & Minh</nuxt-link>
      <a
        role="button"
        class="navbar-burger burger"
        aria-label="menu" aria-expanded="false"
        data-target="navbarMenu"
        @click="toggleNavBarMenu()"
        v-bind:class="{ 'is-active': navbarMenuState }"
      >
        <span aria-hidden="true"></span>
        <span aria-hidden="true"></span>
        <span aria-hidden="true"></span>
      </a>
    </div>
    <div
      id="navbarMenu" class="navbar-menu"
      v-bind:class="{ 'is-active': navbarMenuState }"
    >
      <div class="navbar-end">
        <nuxt-link
          class="navbar-item"
          v-for="(item, key) of items"
          :key="key"
          :to="item.to"
          exact-active-class="is-active"
          @click.native="toggleNavBarMenu()"
        >
          {{ item.title }}
        </nuxt-link>
        <div class="navbar-item">
          <b-button type="is-info" outlined @click="toggleNavBarMenu()">RSVP</b-button>
        </div>
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
        navbarMenuState: false
      };
    },
    methods: {
      toggleNavBarMenu() {
        this.navbarMenuState = !this.navbarMenuState;
      }
    }
  };
</script>
