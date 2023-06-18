<template>
  <form action="" class="container my-3">
    <div class="row">
      <div class="col-md-8">
        <div class="mb-3">
          <label for="" class="form-label">Page Title</label>
          <input type="text" class="form-control" v-model="pageTitle" />
        </div>
        <div class="mb-3">
          <label for="" class="form-label">Content</label>
          <input type="text" class="form-control" rows="5" v-model="content" />
        </div>
      </div>

      <div class="col">
        <div class="mb-3">
          <label for="" class="form-lable">Link Text</label>
          <input type="text" class="form-control" v-model="linkText" />
        </div>
        <div class="mb-3">
          <label for="" class="form-label">Link URL</label>
          <input type="text" class="form-control" v-model="linkUrl" />
        </div>
        <div class="row mb-3">
          <div class="form-check">
            <input
              type="checkbox"
              class="form-check-input"
              v-model="published"
            />
            <label for="gridCheck1" class="form-check-label">Published</label>
          </div>
        </div>
      </div>
    </div>

    <div class="mb-3">
      <button
        class="btn btn-primary"
        :disabled="isFormInvalid"
        @click.prevent="submitForm"
      >
        Create Page
      </button>
    </div>
  </form>
</template>

<script>
export default {
  props: ['pageCreated'],
  computed: {
    isFormInvalid() {
      return (
        !this.pageTitle || !this.content || !this.linkText || !this.linkUrl
      );
    },
  },
  data() {
    return {
      pageTitle: '',
      content: '',
      linkText: '',
      linkUrl: '',
      published: true,
    };
  },
  methods: {
    submitForm() {
      if (!this.pageTitle || !this.content || !this.linkText || !this.linkUrl) {
        alert('Please fill the form');
        return;
      }
      this.pageCreated({
        pageTitle: this.pageTitle,
        content: this.content,
        link: {
          text: this.linkText,
          url: this.linkUrl,
        },
        published: this.published,
      });
      (this.pageTitle = ''),
        (this.content = ''),
        (this.linkText = ''),
        (this.linkUrl = ''),
        (this.published = true);
    },
  },
  watch: {
    pageTitle(newTitle, oldTitle) {
      if (this.linkText === oldTitle) {
        this.linkText = newTitle;
      }
    },
  },
};
</script>

<!-- computed properties - simply return a value. They used the existing data in order to compute a value that is then used in our template. It does not make any change to our state or does not mutate at all.
It simply computes a value based upon the current data.
-->

<!-- watcher properties - watch for a property to change and it gives us the ability to make changes to our state and allow us to mutate our state.  -->
