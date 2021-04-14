<template>
  <div id="app">
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
      <div id="nav">
        <div class="collapse navbar-collapse" id="navbarNavDropdown">
          <ul class="navbar-nav">
            <li class="nav-item active">
              <a class="nav-link" href="#">
                Home
                <span class="sr-only">(current)</span>
              </a>
            </li>
            <!-- <li class="nav-item"><router-link class="nav-link" to="/">Home</router-link></li> -->
            <li class="nav-item"><router-link class="nav-link" to="/about">About</router-link></li>
            <li class="nav-item"><router-link class="nav-link" to="/posts">All Posts</router-link></li>
            <li class="nav-item"><router-link class="nav-link" to="/posts/new">Create a Post</router-link></li>
            <li class="nav-item dropdown">
              <a
                class="nav-link dropdown-toggle"
                href="#"
                id="navbarDropdownMenuLink"
                role="button"
                data-toggle="dropdown"
                aria-haspopup="true"
                aria-expanded="false"
              >
                Account
              </a>
              <div class="dropdown-menu" aria-labelledby="navbarDropdownMenuLink">
                <span v-if="!isLoggedIn()">
                  <router-link class="dropdown-item" to="/login">Login</router-link>
                </span>
                <span>
                  <router-link class="dropdown-item" to="/logout">Logout</router-link>
                </span>
                <span v-if="!isLoggedIn()">
                  <router-link class="dropdown-item" to="/signup">Sign Up</router-link>
                </span>
                <!-- 
                <a class="dropdown-item" href="#">Action</a>
                <a class="dropdown-item" href="#">Another action</a>
                <a class="dropdown-item" href="#">Something else here</a> -->
              </div>
            </li>
          </ul>
        </div>
        <!-- <router-link to="/">Home</router-link>
        |
        <router-link to="/about">About</router-link>
        |
        <router-link to="/posts">All Posts</router-link>
        |
        <router-link to="/posts/new">Create a Post</router-link>
        |
        <router-link to="/signup">Sign Up</router-link>
        |
        <router-link to="/login">Login</router-link>
        |
        <router-link to="/logout">Logout</router-link> -->
      </div>
    </nav>

    <router-view />
  </div>
</template>

<style>
body {
  font-family: Avant Garde, Avantgarde, Century Gothic, CenturyGothic, AppleGothic, sans-serif;
  background-image: url("./assets/background.png");
  margin: 5px;
}
</style>

<script>
export default {
  methods: {
    isLoggedIn: function () {
      return localStorage.getItem("jwt");
    },
  },
};
</script>
