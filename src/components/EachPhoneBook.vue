<template lang="html">
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
  <input type="submit" class="btn btn-primary" value="Delete" v-on:click="remove(book)">
</td>
</tr>
</tbody>
</template>

<script>
export default {
  props: ['books', 'remove']
}
</script>

<style lang="css">
</style>
