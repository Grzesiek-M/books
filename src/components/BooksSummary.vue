<template>
  <p>Books amount : {{books.length}}</p>
  <p>Books price : {{sumPrices}} </p>
</template>

<script>
export default {
  name: 'BooksSummary',
  props: {
    books: {
      type: Array
    }
  },
  // methods: {
  //   booksPrice () {
  //     this.sumPrices = this.books.reduce((this.books, this.books.price), this.sumPrices += this.books.price, 0)
  //     return this.sumPrices
  //   }
  // }
  computed: {
    sumPrices () {
      const sum = this.books.reduce(
        function (result, book) {
          return result + book.price
        },
        0
      )
      return sum
    }
  }
}
</script>
