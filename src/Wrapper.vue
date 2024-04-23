<script>
import OnlineShopping from './components/OnlineShopping.vue';
import Register from './components/Register.vue';
import Wishlist from './components/Wishlist.vue';
import {books} from '../books.js'
    
export default{

    data:()=>({
        active: 'Register',
        books,
        wishlist: []
    }),
    
    methods:{
        submitted(){
            this.active = "OnlineShopping"
        },
          removefromwishlist(book) {
            let bookIndexinBooks = books.findIndex(
              (ibook) => ibook.id == book.id
            );
            this.books[bookIndexinBooks].inwishlist = false;
            let bookIndex = this.wishlist.findIndex(
              (ibook) => ibook.id == book.id
            );
            this.wishlist.splice(bookIndex, 1);
          },
        addtowishlist(book) {
            let bookIndex = books.findIndex((ibook) => ibook.id == book.id);
            this.books[bookIndex].inwishlist = true;
            this.wishlist.push(book);
          },
    },
    
    components: {Register, OnlineShopping, Wishlist}
   }
</script>

<template>
    <div class="w-100 mx-auto text-center">
        <nav style="--bs-breadcrumb-divider: url(&#34;data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='8' height='8'%3E%3Cpath d='M2.5 0L1 1.5 3.5 4 1 6.5 2.5 8l4-4-4-4z' fill='%236c757d'/%3E%3C/svg%3E&#34;);" aria-label="breadcrumb">
            <ol class="breadcrumb justify-content-center">
                <li class="breadcrumb-item"><a href="#" @click.prevent="active = 'Register'">Register</a></li>
                <li class="breadcrumb-item"><a href="#" @click.prevent="active = 'OnlineShopping'">Online Shopping</a></li>
                <li class="breadcrumb-item" ><a href="#" @click.prevent="active = 'Wishlist'">Wishlist</a></li>
            </ol>
        </nav>
        <keep-alive>
            <component :is="active" :books= "books" :wishlist="wishlist" @submitted="submitted" @bookRemoved="removefromwishlist" @bookAdded="addtowishlist"/>
        </keep-alive>
    </div>
</template>

