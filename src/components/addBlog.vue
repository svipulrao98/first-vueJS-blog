<template>
    <div id="add-blog">
        <form v-if="!submitted">
          <h2>Add a New Blog Post</h2>
            <label>Blog Title:</label>
            <input type="text" v-model.lazy="blog.title" required />
            <label>Blog Content:</label>
            <textarea v-model.lazy.trim="blog.content"></textarea>
            <div id="checkboxes">
                <p>Blog Categories:</p>
                <label>Ninjas</label>
                <input type="checkbox" value="ninjas" v-model="blog.categories" />
                <label>Wizards</label>
                <input type="checkbox" value="wizards" v-model="blog.categories" />
                <label>Mario</label>
                <input type="checkbox" value="mario" v-model="blog.categories" />
                <label>Cheese</label>
                <input type="checkbox" value="cheese" v-model="blog.categories" />
            </div>
            <label>Author: </label>
            <select v-model="blog.author">
              <option v-for="author in authors">{{author}}</option>
            </select>
            <button v-on:click.prevent="post">Add Blog</button>
        </form>
        <div v-if="submitted">
          <h2>Thank you!</h2>
          <h4>Post added successfully</h4>
        </div>
        <div id="preview">
            <h3>Preview blog</h3>
            <p>Blog title: {{ blog.title }}</p>
            <p>Blog content:</p>
            <div v-if="submitted">
              <article id = "blog-content-preview" style="white-space: pre">{{ blog.content}}</article>
            </div>
            <p v-if="!submitted" style="white-space: pre">{{ blog.content | snippet }}</p>
            <p>Blog Categories:</p>
            <ul>
                <li v-for="category in blog.categories">{{ category }}</li>
            </ul>
            <p>Author: {{blog.author}}</p>
            <button v-if="submitted" v-on:click="submitted=!submitted">Post Another!</button>
        </div>
    </div>
</template>

<script>
// Imports
export default {
    data () {
        return {
            blog: {
                title: '',
                content: '',
                categories: [],
                author: ''
            },
            authors: ['Vips the man of iron', 'vipul the captain', 'rao the thunder'],
            submitted: false
        }
    },
    methods: {
      post:function(){
        this.$http.post(/*<-Your firebase link->*/, this.blog).then(function(data){
          console.log(data);
          this.submitted=true;
        });
      }
    }
}
</script>

<style>
#add-blog *{
    box-sizing: border-box;
}
#add-blog{
    margin: 20px auto;
    max-width: 500px;
}
label{
    display: block;
    margin: 20px 0 10px;
}
input[type="text"], textarea{
    display: block;
    width: 100%;
    padding: 8px;
}
#preview{
    padding: 10px 20px;
    border: 1px dotted #ccc;
    margin: 30px 0;
}
h3{
    margin-top: 10px;
}
#checkboxes input{
    display: inline-block;
    margin-right: 10px;
}
#checkboxes label{
    display: inline-block;
}
#blog-content-preview{
    max-width: 480px;
    margin: 0 auto;
}
</style>
