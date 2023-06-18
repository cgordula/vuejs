<template>
  <a
    class="nav-link"
    :class="activeClasses"
    :href="page.link.url"
    :title="`This link goes to the ${page.link.text} page`"
    >{{ page.link.text }}</a
  >
</template>

<script>
export default {
  props: ['page', 'isActive'],
  computed: {
    activeClasses() {
      return {
        active: this.isActive,
        emphasize: this.isActive,
      };
    },
  },
};
</script>

<!-- adding styles in PageViewer.vue -->
<!-- Without 'scoped' the text-decoraton underline will show also not only on the Navbar but also in the pageViewer (it will be global) -->
<style scoped>
.emphasize {
  text-decoration: underline !important;
}
</style>
