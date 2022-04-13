<template>
  <div class="app">

    <!-- heading -->
    <header class="app__heading">
      <h1>Books<span>.app</span></h1>
    </header>
    <!-- books list -->
    <BooksList
    :books="books"
    @remove="removeBook" />
    <BooksLengthMsg
    :length="books.length"
     />
     <BookForm
    @add="handleSubmit"
     />
     <BooksSummary
     :books="books"
     />

  </div>
</template>

<script>
import BooksList from './components/BooksList'
import BooksLengthMsg from './components/BooksLengthMsg.vue'
import BookForm from './components/BookForm.vue'
import BooksSummary from './components/BooksSummary.vue'
export default {
  name: 'App',
  components: {
    BooksList,
    BooksLengthMsg,
    BookForm,
    BooksSummary
  },
  data: () => ({
    books: [
      {
        title: 'The Catcher in the Rye',
        price: 20
      },
      {
        title: 'Of Mice and Men',
        price: 18
      }
    ]
  }),
  created () {
    fetch('https://cors-anywhere.herokuapp.com/https://api.itbook.store/1.0/search/mongodb', {
      headers: {
        accept: '*/*',
        'accept-language': 'en-US,en;q=0.9',
        'sec-ch-ua': '" Not A;Brand";v="99", "Chromium";v="99", "Google Chrome";v="99"',
        'sec-ch-ua-mobile': '?0',
        'sec-ch-ua-platform': '"macOS"',
        'sec-fetch-dest': 'empty',
        'sec-fetch-mode': 'cors',
        'sec-fetch-site': 'cross-site'
      },
      referrerPolicy: 'strict-origin-when-cross-origin',
      body: null,
      method: 'GET',
      mode: 'cors',
      credentials: 'omit'
    })
      .then((response) => response.json())
      .then((data) => {
        this.books = data.books.slice(0, 3).map((book) => {
          book.price = parseFloat(book.price.replace('$', ''))
          return book
        })
      })
  },
  methods: {
    removeBook (index) {
      this.books.splice(index, 1)
    },
    handleSubmit (book) {
      this.books.push({ ...book })
      console.log(this.books)
    }
  }
}
</script>

<style lang="scss" scoped>
.app {
  width: 100%;
  max-width: 1000px;
  padding: 2rem;
  margin: 0 auto;

  &__heading {
    font-size: 3rem;
    text-align: center;
    span {
      color: #5a58da;
    }
  }
}
</style>
