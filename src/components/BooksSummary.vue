<template>
  <p>Books amount: {{ books.length }}</p>
  <p>Books price: {{ booksTotal }}</p>
</template>

<script>
export default {
  name: 'BooksSummary',
  props: {
    books: {
      type: Array,
      required: true
    }
  },
  computed: {
    booksTotal: function () {
      return this.books.reduce((total, book) => total + book.price, 0)
    }
  }
}
</script>
