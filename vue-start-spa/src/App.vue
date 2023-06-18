<template>
  <navigation-bar
    :pages="pages"
    :active-page="activePage"
    :nav-link-click="(index) => (activePage = index)"
  >
  </navigation-bar>
  <page-viewer :page="pages[activePage]"> </page-viewer>
</template>

<script>
import NavigationBar from './components/NavigationBar.vue';
import PageViewer from './components/PageViewer.vue';

export default {
  components: {
    NavigationBar,
    PageViewer,
  },
  created() {
    this.getPages();
  },
  data() {
    return {
      activePage: 0,
      pages: [],
    };
  },
  methods: {
    async getPages() {
      let res = await fetch('page.json');
      let data = await res.json();

      this.pages = data;
    },
  },
};
</script>
