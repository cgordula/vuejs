<template>
  <navigation-bar
    :pages="pages"
    :active-page="activePage"
    :nav-link-click="(index) => (activePage = index)"
  >
  </navigation-bar>

  <!-- v-show uses css to hide content  -->
  <div v-show="false">hide content</div>

  <!-- v-if does not output element at all if it is false and it is simple approach when using props-->
  <!-- <page-viewer v-if="pages.length > 0" :page="pages[activePage]"> </page-viewer> -->

  <!-- <page-viewer :page="pages[activePage]"> </page-viewer> -->

  <create-page :page-created="pageCreated"> </create-page>
</template>

<script>
/* eslint-disable */
import NavigationBar from './components/NavigationBar.vue';
import PageViewer from './components/PageViewer.vue';
import CreatePage from './components/CreatePage.vue';

export default {
  components: {
    NavigationBar,
    PageViewer,
    CreatePage,
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
      let res = await fetch('pages.json');
      let data = await res.json();

      this.pages = data;
    },
    pageCreated(pageObj) {
      console.log(pageObj);
    },
  },
};
</script>
