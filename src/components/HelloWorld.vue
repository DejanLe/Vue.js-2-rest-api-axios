<template>
  <div class="news">
    <div class="container">
        <div class="row">
           <div class="col-md-12">

            <ul v-if="posts && posts.length">
             
                  <li v-for=" post of posts">
                    <div class="panel panel-default">
                      <div class="panel-heading">
                        <h3> <strong>{{post.title}}  </strong> </h3>
                      </div>
                      <div class="panel-body">
                        <p>{{post.body}}  </p>
                      </div> 
                    </div>
                 </li> 
              
            </ul>
           <ul v-if="errors && errors.length">
            <li v-for="error of errors"> 
              {{error.message}}
            </li>
           </ul>
         </div>
      </div> 
       
    </div> 
  </div>
</template>

<script>
import axios from 'axios';
 
 export default {
  data(){
    return{
      posts:[],
      errors: []
    }
  },
  //Fetch posts when the component is created.
  created(){
    axios.get(`http://jsonplaceholder.typicode.com/posts`)
    .then(response =>{
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
 
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.panel{
  max-width:50rem;
  width:100%; 
}
</style>
