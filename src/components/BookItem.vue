<template>
  <div
  :class="{
    'books-list__item--promotion': isPromotion
  }"
  >
    {{ book.title }}, {{ book.price }}$
  </div>
  <button @click="$emit('remove', index)" class="book-list__btn">Remove</button>
</template>

<script>
export default {
  name: 'BookItem',
  props: {
    book: {
      type: Object,
      required: true
    },
    index: {
      type: Number,
      required: true
    }
  },
  computed: {
    isPromotion: function () {
      return this.book.price < 20
    }
  }
}
</script>

<style lang="scss" scoped>

  .book-list__btn {
    color: #fff;
    box-shadow: 0 10px 40px 0 rgba(76,104,239,.35), 0 0 20px 0 rgba(76,104,239,.05);
    border-radius: .3rem;
    border: none;
    font-family: inherit;
    text-transform: uppercase;
    font-weight: 700;
    min-width: 6rem;
    text-align: center;
    cursor: pointer;
    transition: .2s;
    background: #ea2027;
    color: #fff;
    padding: .5rem 1rem;
    font-size: .6rem;
    margin: 0 .5rem;

    &:hover {
      box-shadow: 0 20px 40px 0 rgba(76,104,239,.35);
    }
  }
  .books-list__item--promotion {
    font-size: 1.5rem;
    text-decoration: underline;
  }
</style>
