<template>
 <!-- no books message -->
  <p v-if="length > 5">{{ length }} books</p>
  <p v-else-if="length > 1">Not too many of them</p>
  <p v-else-if="length === 1">One single book</p>
  <p v-else>Go get some books</p>
</template>

<script>
export default {
  name: 'BooksLengthMsg',
  props: {
    length: {
      type: Number,
      required: true
    }
  }
}
</script>
