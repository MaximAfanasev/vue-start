<template>
  {{ name }}
  {{ surn }}

  <button @click="handle">btn</button>
</template>

<script>
export default {
  props: {
    name: String,
    surn: String,
    title: String,
    likes: Number,
    isPublished: Boolean,
    commentIds: Array,
    author: Object,
    callback: Function,
    contactsPromise: Promise // или любой другой конструктор
  },
  data() {
    return {
      name: 'john',
    }
  },
  methods: {
    handle() {
      this.$emit('show', 'xxx', 'yyy');
    },
  }
}
</script>

<style scoped>

</style>