<template>
  <div id="app">
    <header>
      <h1>Cooking Masterclass</h1>
      <p>Wishlist ({{ wishlist.length }})</p>
    </header>
    <CourseCatalogue @add-to-wishlist="addToWishlist" />
    <section class="wishlist">
      <h2>This Is Your Wishlist:</h2>
      <ul>
        <li v-for="course in wishlist" :key="course.id">
          {{ course.title }} (R{{ course.price }})
        </li>
      </ul>
    </section>
  </div>
</template>

<script>
import CourseCatalogue from './components/CourseCatalogue.vue'

export default {
  name: 'App',
  components: { CourseCatalogue },
  data() {
    return {
      wishlist: []
    }
  },
  methods: {
    addToWishlist(course) {
      if (!this.wishlist.includes(course)) {
        this.wishlist.push(course)
      }
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  max-width: 800px;
  margin: 60px auto;
  padding: 20px;
  background-image: url('/images/background24.webp');
  background-size: contain;
  background-position: center;
  background-repeat: no-repeat;
  border: 1px solid #ddd;
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

header {
  background-color: #4CAF50;
  padding: 20px;
  border-bottom: 1px solid #ddd;
  color: #fff;
}

.wishlist {
  margin-top: 40px;
}

.wishlist ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.wishlist li {
  margin-bottom: 10px;
}

.course-catalogue {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}

.course-card {
  margin: 20px;
  padding: 20px;
  border: 1px solid #ddd;
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  width: calc(33.33% - 40px);
  background-color: #fff;
}

.course-card img {
  width: 100%;
  height: 150px;
  object-fit: cover;
  border-radius: 10px 10px 0 0;
}

.course-card h2 {
  font-size: 18px;
  margin-bottom: 10px;
}

.course-card p {
  font-size: 14px;
  color: #666;
}

.course-card button {
  background-color: #4CAF50;
  color: #fff;
  border: none;
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
}

.course-card button:hover {
  background-color: #3e8e41;
}
</style>