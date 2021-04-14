<template>
  <div class="posts-new">
    <h2>Add a post.</h2>
    <div class="form-group">
      <label for="formGroupExampleTitle">Title:</label>
      <input type="text" class="form-control" id="formGroupExampleInput" placeholder="Title" v-model="postTitle" />
    </div>
    <div class="form-group">
      <label for="formGroupExampleContent">Content:</label>
      <input type="text" class="form-control" id="formGroupExampleInput" placeholder="Content" v-model="postBody" />
      <small v-if="postBody.length > 0 && postBody.length < 200">
        {{ 200 - postBody.length }} characters remaining.
      </small>
    </div>
    <div class="form-group">
      <label for="formGroupExampleImage">Image:</label>
      <input type="text" class="form-control" id="formGroupExampleImage" placeholder="Image" v-model="postImage" />
    </div>
    <p>
      <button v-on:click="createPost()" class="btn btn-secondary">Add Post</button>
    </p>
    <!-- </div> -->
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      postTitle: "",
      postBody: "",
      postImage: "",
    };
  },
  created: function () {
    // this.indexPlaces();
  },
  methods: {
    createPost: function () {
      console.log("Adding a Post!");
      var params = {
        title: this.postTitle,
        body: this.postBody,
        image: this.postImage,
      };
      axios
        .post("/api/posts", params)
        .then(() => {
          this.$router.push("/posts");
        })
        .catch((error) => console.log(error.response));
    },
  },
};
</script>
