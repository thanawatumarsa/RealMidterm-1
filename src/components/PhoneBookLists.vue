<template lang="html">
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
    <each-phone-book :books="books" :remove="remove"></each-phone-book>
  </table>
</template>

<script>

import EachPhoneBook from '../components/EachPhoneBook'
export default {
  props: ['books', 'remove'],
  components: {
    EachPhoneBook
  }
}
</script>

<style lang="css">
</style>
