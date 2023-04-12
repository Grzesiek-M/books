<template>
  <p>Books amount : {{books.length}}</p>
  <p>Books price : {{sumPrices}} </p>
  <p>Books price : {{books.booksPrice}} </p>
</template>

<script>
export default {
  name: 'BooksSummary',
  props: {
    books: {
      type: Array
    }
  },
  methods: {
    booksPrice () {
      this.sumPrices = this.books.reduce((this.books, this.books.price), this.sumPrices += this.books.price, 0)
      return this.sumPrices
    }
  }
}
</script>
