<template>
  <div class="posts-show">
    <div class="container">
      <!-- <div v-for="post in posts" v-bind:key="post.id"> -->
      <h3>{{ post.title }}</h3>
      <img v-bind:src="post.image" v-bind:alt="post.title" />
      <br />
      {{ post.body }}
      <br />
      <router-link v-bind:to="`/posts/${post.id}/edit`">More info...</router-link>
    </div>
    <br />
    <button v-on:click="destroyPost(post)">Delete Post</button>
    <!-- </div> -->
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      post: {},
    };
  },
  created: function () {
    this.showPosts();
  },
  methods: {
    showPosts: function () {
      axios.get("/api/posts/" + this.$route.params.id).then((response) => {
        this.post = response.data;
        console.log("All Posts:", this.post);
      });
    },
    destroyPost: function (post) {
      axios.delete("/api/posts/" + post.id).then(() => {
        console.log("Post deleted.");
        this.$router.push("/posts");
      });
    },
  },
};
</script>
