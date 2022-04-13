<template>
  <!-- books list -->
  <ul class="book-list">
    <li :key="index" v-for="(book, index) in books" class="book-list__item">
      <BookItem
      :book="book"
      :index="index"
      @remove="$emit('remove', index)"
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

<style lang="scss" scoped>
.books-list {
  font-size: 1rem;
  list-style-type: none;
  margin: 1rem 0;
  padding: 1rem;
  color: #637892;
  font-weight: 700;

  &__item {
    padding: 1rem 0;
    border-bottom: .0625rem dashed rgba(0,0,0,.1);
  }

}
</style>
