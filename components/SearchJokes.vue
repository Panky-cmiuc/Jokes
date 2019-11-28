<template>
  <form @submit.prevent="onSubmit">
    <input type="text" v-model="text" placeholder="Search Jokes...">
    <input type="submit" value='Search Jokes'>
    <!-- <input type="text" v-model="searchTerm" placeholder="Search Jokes..." hidden> -->
    <label style="display:flex; margin-top:10px">Search Term: {{searchTerm}}</label>
  </form>
</template>

<script>
export default {
  name: 'SearchJokes',
  data(){
    return{
      text:'',
      searchTerm:''
    }
  },
  methods:{
    onSubmit(){
      this.$emit('search-text', this.text);
      this.searchTerm=this.text;
      this.text='';
    }
  }
}
</script>
