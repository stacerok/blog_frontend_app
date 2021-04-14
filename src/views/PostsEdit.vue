<template>
  <div class="posts-edit">
    <form v-on:submit.prevent="updatePost(post)">
      <h1>Edit Post</h1>
      <ul>
        <li class="text-danger" v-for="error in errors" v-bind:key="error">
          {{ error }}
        </li>
      </ul>
      <div class="form-group">
        <label>Title:</label>
        <input type="text" class="form-control" v-model="post.title" />
      </div>
      <div class="form-group">
        <label>Image:</label>
        <input type="text" class="form-control" v-model="post.image" />
      </div>
      <div class="form-group">
        <label>Body:</label>
        <input type="text" class="form-control" v-model="post.body" />
      </div>
      <br />
      <input type="submit" class="btn btn-primary" value="Update" />
    </form>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data: function () {
    return {
      post: {},
      errors: [],
    };
  },
  created: function () {
    axios.get("/api/posts/" + this.$route.params.id).then((response) => {
      console.log(response.data);
      this.post = response.data;
    });
  },
  methods: {
    updatePost: function (post) {
      console.log("Updating post.");
      var params = {
        title: post.title,
        image: post.image,
        body: post.body,
      };
      axios
        .patch("/api/posts/" + this.$route.params.id, params)
        .then(() => {
          this.$router.push("/posts/" + this.post.id);
        })
        .catch((error) => console.log(error.response));
    },
  },
};
</script>
