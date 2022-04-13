<template>
  <!-- books list -->
  <ul>
    <li :key="index" v-for="(book, index) in books">
      <BookItem
      :book="book"
      :index="index"
      />
    </li>
  </ul>

</template>

<script>
import BookItem from './BookItem.vue'

export default {
  name: 'BooksList',
  components: { BookItem },
  props: {
    books: {
      type: Array,
      required: true
    }
  }
}
</script>
