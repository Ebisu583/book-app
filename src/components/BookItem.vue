<template>
  {{ book.title }}, {{ book.price }}$
  <button @click="$emit('remove', index)">Remove</button>
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
  }
}
</script>
