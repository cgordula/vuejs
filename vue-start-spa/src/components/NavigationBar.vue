<template>
  <nav
    :class="[`navbar-${theme}`, `bg-${theme}`, 'navbar', 'navbar-expand-lg']"
  >
    <div class="container-fluid">
      <a class="navbar-brand" href="#">My Vue</a>
      <button
        class="navbar-toggler"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#navbarSupportedContent"
        aria-controls="navbarSupportedContent"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav me-auto mb-2 mb-lg-0">
          <li v-for="(page, index) in pages" :key="index" class="nav-item">
            <navbar-link
              :page="page"
              :isActive="activePage === index"
              @click.prevent="navLinkClick(index)"
            ></navbar-link>
          </li>
        </ul>
        <form class="d-flex">
          <button
            class="btn btn-outline-success"
            @click.prevent="changeTheme()"
          >
            On/Off
          </button>
        </form>
      </div>
    </div>
  </nav>
</template>

<script>
import NavbarLink from './NavbarLink.vue';

export default {
  components: {
    NavbarLink,
  },
  props: ['pages', 'activePage', 'navLinkClick'],
  data() {
    return {
      theme: 'light',
    };
  },
  methods: {
    changeTheme() {
      this.theme = this.theme === 'light' ? 'dark' : 'light';
    },
  },
};
</script>
