<template>
  <div class="hello">

  <h1>{{msg}}</h1>
  <ul v-if="posts && posts.length">
    <li v-for="post of posts">
    <p><strong>{{post.title}}</strong></p>
    <p>{{post.body}}</p>
    </li>
    </ul>

    <ul v-if="errors && errors.length">
      <li v-for="error of errors">
      {{error.message}}
      </li>
      </ul>

  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      posts:[],
      errors:[]
    }
  },
  created(){
  axios.get(`http://jsonplaceholder.typicode.com/posts`)
  .then(response => {
  this.posts = response.data
  })
  .catch(e => {
  this.errors.push(e)
  })
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
