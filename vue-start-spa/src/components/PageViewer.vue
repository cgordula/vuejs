<template>
  <div class="container">
    <h1 class="emphasize">{{ page.pageTitle }}</h1>
    <p>{{ page.content }}</p>
  </div>
</template>

<script>
export default {
  // props: ['page'],
  // another approach if you have a component that has a lot of different props using object
  props: {
    page: {
      types: Object,
      default() {
        return {
          pageTitle: '',
          content: '',
        };
      },
    },
  },
};
</script>

<!-- to add a separate style you can add style in this page -->
<style>
.emphasize {
  color: blue;
}
</style>
