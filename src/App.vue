
<template>
  <div id="app" class="app">

    <!-- heading -->
    <header>
      <h1 class="app__heading">Books<span>.app</span></h1>
    </header>
    <!-- books list -->
    <books-list @remove="removeBook" :books="books" />
    <books-Length-Msg :length="books.length" />
    <book-form @add="addBook" />
    <books-summary :books="books" />

    <!-- add book form -->
  </div>
</template>

<script>
import { ref } from 'vue'
import BooksList from './components/BooksList'
import BooksLengthMsg from './components/BooksLengthMsg'
import BookForm from './components/BookForm'
import BooksSummary from './components/BooksSummary.vue'
const ebook = ref(null)

fetch('https://api.itbook.store/1.0/new')
  .then((response) => response.json())
  // .then((data) => {
  //   this.books.value.push(data)
  //   console.log(data)
  // })
  // .then((data) => {
  //   console.log(data)
  //   this.form.push(data)
  //   console.log(this.books)
  // })
  .then((data) => {
    console.log(ebook)
    console.log(data)
    this.books.push(...data.ebooks.splice(0, 3))
  })

export default {

  name: 'App',
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
    ],
    form: {
      title: '',
      price: 0
    },
    ebook: {
      title: '',
      price: 0
    }

  }),
  components: {
    BooksList,
    BooksLengthMsg,
    BookForm,
    BooksSummary
  },
  methods: {
    removeBook (index) {
      this.books.splice(index, 1)
    },
    addBook (book) {
      this.books.push({ ...book })
    },
    lengthBook (book) {
      this.books({ ...book.length })
    }
  }
}

</script>

<style lang="scss">
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
