<template>
  <div class="container">
    <SearchUser/>
    <ListUser/>
  </div>
</template>

<script>
import ListUser from './components/ListUser.vue'
import SearchUser from './components/SearchUser.vue';

export default {
  name:'App',
  components:{
    ListUser,
    SearchUser
  }
}
</script>

<style>

</style>