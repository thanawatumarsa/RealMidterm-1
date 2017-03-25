<template lang="html">
  <form id="form" class="form-inline" v-on:submit.prevent="addphonebook">
    <div class="form-group">
      <input type="text" id="name" class="form-control" placeholder="ชื่อ" v-model="newphonebook.name">
    </div>
    <div class="form-group">
      <input type="text" id="phone" class="form-control" placeholder="เบอร์โทร" v-model="newphonebook.phone">
    </div>
    <div class="form-group">
      <input type="text" id="email" class="form-control" placeholder="Email" v-model="newphonebook.email">
    </div>
    <input :disabled="newphonebook.name == '' || newphonebook.phone == '' || newphonebook.email == ''"type="submit" class="btn btn-default" value="+ Add">
  </form>
</template>

<script>
export default {
  props: ['addphonebook', 'newphonebook']
}
</script>

<style lang="css">
</style>
