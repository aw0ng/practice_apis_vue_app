<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <!-- <div v-for="post in redditPosts" v-bind:key="post.data.name">{{ post.data.title }}</div> -->
    <div v-for="headline in headlines" v-bind:key="headline.author">{{ headline.title }}</div>
  </div>
</template>

<style></style>

<script>
import axios from "axios";

export default {
  data: function() {
    return {
      message: "Welcome to Vue.js!",
      todos: [],
      redditPosts: [],
      headlines: [],
    };
  },
  created: function() {
    // axios.get("https://jsonplaceholder.typicode.com/todos").then(response => {
    //   console.log(response.data);
    //   this.todos = response.data;
    // });
    axios.get("/api/redditposts").then(response => {
      console.log(response.data);
      this.redditPosts = response.data.children;
    });
    axios.get("/api/newsheadlines").then(response => {
      console.log(response.data);
      this.headlines = response.data.articles;
    });
  },
  methods: {
    // createTodo: function() {
    //   var params = {
    //     completed: this.newCompleted,
    //     title: this.newTitle,
    //     userId: this.newUserId,
    //   };
    //   axios.post("https://jsonplaceholder.typicode.com/todos", params).then(response => {
    //     console.log("todos create", response);
    //     this.todos.push(response.data);
    //   });
    // },
  },
};
</script>
