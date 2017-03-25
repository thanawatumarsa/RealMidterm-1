<template>
  <div id="app" class="container">
    <div class="page-header">
      <h1>phoneBook</h1>
    </div>
        <table class="table table">
          <thead>
            <tr>
              <th>
                #
              </th>
              <th>
                ชื่อ
              </th>
              <th>
                เบอร์โทร
              </th>
              <th>
                Email
              </th>
              <th>
                Delete
              </th>
            </tr>
          </thead>
          <tbody>
      <tr  v-for="(book, index) in books">
        <td>
          {{index + 1}}
        </td>
        <td>
          {{book.name}}
        </td>
        <td>
          {{book.phone}}
        </td>
        <td>
          {{book.email}}
        </td>
        <td>
          <input type="submit" class="btn btn-primary" value="Delete" v-on:click="removePhoneBook(book)">
        </td>
      </tr>
        </tbody>
        </table>
        <form id="form" class="form-inline" v-on:submit.prevent="addPhoneBook">
          <div class="form-group">
            <input type="text" id="name" class="form-control" placeholder="ชื่อ" v-model="newPhoneBook.name">
          </div>
          <div class="form-group">
            <input type="text" id="phone" class="form-control" placeholder="เบอร์โทร" v-model="newPhoneBook.phone">
          </div>
          <div class="form-group">
            <input type="text" id="email" class="form-control" placeholder="Email" v-model="newPhoneBook.email">
          </div>
          <input type="submit" class="btn btn-default" value="+ Add">
      </form>
  </div>
</template>
<script>

import Firebase from 'firebase'

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
