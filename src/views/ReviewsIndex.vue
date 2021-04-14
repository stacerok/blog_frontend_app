<template>
  <div class="postsindex">
    <div class="container">
      <div class="row" v-for="post in posts" v-bind:key="post.id">
        <div class="col">
          <div class="card">
            <div class="card-body">
              <h5 class="card-title">{{ post.title }}</h5>
              <p class="card-text">{{ post.body }}</p>
              <router-link v-bind:to="`posts/${post.id}`">
                <button type="button" class="btn btn-secondary">More Info...</button>
              </router-link>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      posts: [],
    };
  },
  created: function () {
    this.indexPosts();
  },
  methods: {
    indexPosts: function () {
      axios.get("/api/posts").then((response) => {
        this.posts = response.data;
        console.log("All Posts:", this.posts);
      });
    },
  },
};
</script>
