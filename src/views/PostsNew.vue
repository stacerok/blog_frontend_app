<template>
  <div class="postsnew">
    <div>
      <h2>Add a post.</h2>
      <p>
        Title:
        <input type="text" placeholder="Title" v-model="postTitle" />
      </p>
      <p>
        Content:
        <input type="text" placeholder="Content" v-model="postBody" />
      </p>
      <p>
        Image:
        <input type="text" placeholder="Image" v-model="postImage" />
        <br />
      </p>
      <p>
        <button v-on:click="createPost()">Add Post</button>
      </p>
    </div>
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
