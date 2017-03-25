<template>
  <div id="app" class="container">
    <div class="page-header">
      <h1>phoneBook</h1>
    </div>
    <phone-book-lists :books = "books" :remove = "removePhoneBook"></phone-book-lists>
    <add-from :addphonebook = "addPhoneBook" :newphonebook = "newPhoneBook"></add-from>
  </div>
</template>
<script>

import Firebase from 'firebase'

import PhoneBookLists from './components/PhoneBookLists'
import AddFrom from './components/AddFrom'

let config = {
  apiKey: 'AIzaSyBlVjSOp6Nn0fIa6-ibSJUm1DNjGjN4w4g',
  authDomain: 'phonebook-b6892.firebaseapp.com',
  databaseURL: 'https://phonebook-b6892.firebaseio.com',
  storageBucket: 'phonebook-b6892.appspot.com',
  messagingSenderId: '846496908896'
}

let app = Firebase.initializeApp(config)
let db = app.database()

let phoneBooksRef = db.ref('books')

export default {
  name: 'app',
  firebase: {
    books: phoneBooksRef
  },
  data () {
    return {
      newPhoneBook: {
        name: '',
        phone: '',
        email: ''
      }
    }
  },
  components: {
    PhoneBookLists,
    AddFrom
  },
  methods: {
    addPhoneBook: function () {
      phoneBooksRef.push(this.newPhoneBook)
      this.newPhoneBook.name = ''
      this.newPhoneBook.phone = ''
      this.newPhoneBook.email = ''
    },
    removePhoneBook: function (book) {
      phoneBooksRef.child(book['.key']).remove()
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
