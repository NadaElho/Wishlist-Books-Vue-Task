<script>
     export default{
        data: () => ({
        }),
        methods: {
          removefromwishlist(book) {
           this.$emit("bookRemoved", book)
          },
          formatCurrency(price) {
            return Intl.NumberFormat("en-US", {
              style: "currency",
              currency: "USD",
              minimumFractionDigits: 2,
            }).format(price);
          },
        },
        props:['books', 'wishlist']
     }

</script>
<template>
   <div>
        <h5 class="text-danger text-center" v-if="wishlist.length == 0">
          No items in wishlist
        </h5>
        <div class="row justify-content-center gap-2 align-items-baseline">
          <div
            class="card"
            style="width: 18rem"
            v-for="book in wishlist"
            :key="book.id"
          >
            <img :src="book.image" class="card-img-top" alt="..." />
            <div class="card-body">
              <h5 class="card-title">{{book.name}}</h5>
              <div class="row justify-content-between mt-2 align-items-center">
                <div class="col"><span>{{book.category}}</span></div>
                <div class="col"><span>{{book.numberOfPages}} pages</span></div>
              </div>
              <div class="row justify-content-between align-items-center mt-2">
                <span class="col">By {{book.author}}</span>
                <span class="col">{{formatCurrency(book.price)}}</span>
              </div>
              <div class="my-2">ISBN: {{book.ISBN}}</div>
              <button class="btn btn-primary" @click="removefromwishlist(book)">
                Remove from wishlist
              </button>
            </div>
          </div>
        </div>
      </div>
</template>

<style scoped>

</style>
