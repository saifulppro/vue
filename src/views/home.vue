<template>
    <div class="container mx-auto">
        <button class="btn-primary mt-4" @click="addPost">Add Post</button>
    <br>
 
    <h1>All Post</h1>
    <ul>
      <single-post
          style="margin-bottom: 10px"
          v-for="(post, index) in posts"
          :key="index"
          :post="post"
          @delete="handleDelete($event)"
          @fav="handleFav($event)"
      />
    </ul>
    <br>
    <h1>Fabourite post</h1>
    <ul>
      <single-post
          style="margin-bottom: 10px"
          v-for="(post, index) in favs"
          :key="index"
          :post="post"
          @delete="handleDelete($event)"
          @fav="handleFav($event)"
      />
    </ul>
    <br>
    <h1>un fabourite</h1>
    <ul>
      <single-post
          style="margin-bottom: 10px"
          v-for="(post, index) in unFavs"
          :key="index"
          :post="post"
          @delete="handleDelete($event)"
          @fav="handleFav($event)"
      />
    </ul>
    </div>
   
</template>
  
  <script>
  import SinglePost from "@/views/SinglePost.vue";
  export default {
    name: "HomePage",
    components: {SinglePost},
    data() {
      return {
        message: "Hello Bangladesh",
        posts: [
          {
            id: 1,
            title: "Post 1",
            fav: true
          },
          {
            id: 2,
            title: "Post 2",
            fav: false
          },
          {
            id: 3,
            title: "Post 3",
            fav: true
          }
        ],
      }
    },

    computed: {
      favs() {
        return this.posts.filter(post => post.fav)
      },
      unFavs() {
        return this.posts.filter(post => !post.fav)
      },
    },

    methods: {
      handleDelete(post) {
        this.posts = this.posts.filter(p => p.id !== post.id)
      },
      addPost() {
        this.posts.push({
          id: this.posts.length + 1,
          title: `Post ${this.posts.length + 1}`
        })
      },
      handleFav(post) {
        this.posts = this.posts.map(p => {
          if (p.id === post.id) {
            p.fav = !p.fav
          }
          return p
        })
      }
    }
  }
  </script>
  
  <style scoped>
  h1 {
    color: green;
  }
  </style>