<template>
    <!-- <div>
        <app-header v-bind:title="title" v-on:changeTitle="updateTitle($event)"></app-header>
        <app-ninjas v-bind:ninjas="ninjas"></app-ninjas>
        <ul>
          <li v-for="ninja in ninjas">{{ ninja.name }}</li>
        </ul>
        <app-footer v-bind:title="title"></app-footer>
    </div> -->
    <div>
      <!-- <form-helper>
        <div slot="form-header">
          <h3>This is ME</h3>
          <p>This is all you need to know about me, NOTHING</p>
        </div>
        <div slot="form-fields">
          <input type="text" placeholder="name" required />
          <input type="password" placeholder="password" required />
        </div>
        <div slot="form-controls">
          <button on:click="handleSubmit">Submit</button>
        </div>
      </form-helper> -->
      <!-- <keep-alive>
        <component v-bind:is="component"></component>
      </keep-alive>
      <button v-on:click="component='form-one'">Show form One</button>
      <button v-on:click="component='form-two'">Show form Two</button> -->
      <!-- <show-blog></show-blog>
      <list-blog></list-blog> -->
      <app-header></app-header>
      <router-view></router-view>
    </div>
</template>

<script>
// Imports
// import Header from './components/Header.vue';
// import Footer from './components/Footer.vue';
// import Ninjas from './components/Ninjas.vue';
// import formHelper from './components/formHelper.vue'
// import formOne from './components/formOne.vue';
// import formTwo from './components/formTwo.vue';
import addBlog from './components/addBlog.vue';
import showBlogs from './components/showBlogs.vue';
import listBlogs from './components/listBlogs.vue';
import header from './components/header.vue';

export default {
    components: {
        // 'app-header': Header,
        // 'app-footer': Footer,
        // 'app-ninjas': Ninjas
        // 'form-helper': formHelper
        // 'form-one': formOne,
        // 'form-two': formTwo
        'add-blog': addBlog,
        'show-blog': showBlogs,
        'list-blog': listBlogs,
        'app-header': header
    },
    data(){
      return{
        // component: 'form-one'
      }
    },
    methods:{

    }
    // data () {
    //     return {
    //       ninjas: [
    //           {name: 'Ryu', speciality: 'Vue Components', show: false},
    //           {name: 'Crystal', speciality: 'HTML Wizardry', show: false},
    //           {name: 'Hitoshi', speciality: 'Click Events', show: false},
    //           {name: 'Tango', speciality: 'Conditionals', show: false},
    //           {name: 'Kami', speciality: 'Webpack', show: false},
    //           {name: 'Yoshi', speciality: 'Data Diggin', show: false}
    //       ],
    //       title: 'Vue Wizards'
    //     }
    // },
    // methods: {
    //   updateTitle: function(updatedTitle){
    //     this.title = updatedTitle;
    //   }
    // }
}
</script>

<style>
body{
    margin: 0;
    font-family: 'Nunito SemiBold';
}
</style>
