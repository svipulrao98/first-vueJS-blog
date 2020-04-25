<template>
    <div id="show-blogs">
        <h1>All Blog Articles</h1>
        <input type="text" v-model="search" placeholder="search blogs" />
        <div v-for="blog in filteredBlogs" class="single-blog">
            <router-link v-bind:to="'blog/' +blog.id"><h2>{{ blog.title }}</h2></router-link>
            <article>{{ blog.content | snippet }}</article>
        </div>
    </div>
</template>

<script>
// Imports
import searchMixin from '../mixins/searchMixin';
export default {
    data () {
        return {
            blogs: [],
            search: ''
        }
    },
    created() {
        this.$http.get('https://timepass-7e081.firebaseio.com/posts.json').then(function(data){
          return data.json();
        }).then(function(data){
          var blogArray=[];
          for(let key in data){
            // console.log(data[key]);
            data[key].id = key;
            blogArray.push(data[key]);
          }
          this.blogs=blogArray;
        });
    },
    mixins: [searchMixin]
}
</script>

<style>
#show-blogs{
    max-width: 800px;
    margin: 0px auto;
}
.single-blog{
    padding: 20px;
    margin: 20px 0;
    box-sizing: border-box;
    background: #eee;
}
</style>
