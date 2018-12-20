<template>
  <div class="testing">
    <h2>External Api Data Test</h2>
    <ul>
      <li v-for="(post, index) of posts" :key="index">
        <p>{{ post.id }}. {{ post.title }}</p>
      </li>
    </ul>
    
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'ApiTest',
  data () {
    return {
      posts: [],
      errors: []
    }
  },
  created() {
    axios.get(`https://jsonplaceholder.typicode.com/todos`)
    .then(res => {
      this.posts = res.data
      console.log(this.posts)
    })
    .catch(err => {
      this.errors.push(err)
    })
    
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
 li {
   list-style: none;
 }

</style>
