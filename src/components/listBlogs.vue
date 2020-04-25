<template>
    <div id="show-blogs">
        <h1>List Blog Titles</h1>
        <input type="text" v-model="search" placeholder="search blogs" />
        <div v-for="blog in filteredBlogs" class="single-blog">
            <h2>{{ blog.title }}</h2>
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
        this.$http.get(/*<-Your firebase link->*/).then(function(data){
          return data.json();
        }).then(function(data){
          var blogArray = [];
          for(let key in data){
            data[key].id = key;
            blogArray.push(data[key]);
          }
          this.blogs = blogArray;
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
