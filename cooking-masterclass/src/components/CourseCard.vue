<template>
  <div class="course-card">
    <img :src="course.image" alt="Course Image"></img>
    <h2>{{ course.title }}</h2>
    <p>Chef: {{ course.chef }}</p>
    <p>Price: R{{ course.price }}</p>
    <p>Skill Level: {{ course.skillLevel }}</p>
    <p v-if="!course.available" class="sold-out">Sold Out</p>
    <button @click="$emit('addToWishlist', course)">Add To Wishlist</button>
  </div>
</template>

<script>
export default {
  name: 'CourseCard',
  props: {
    course: Object
  },
  methods: {
    addToWishlist() {
      this.$emit('add-to-wishlist', this.course)
    }
  }
}
</script>

<style scoped>
.course-card {
  background-color: #f9f9f9;
  padding: 20px;
  border: 1px solid #ddd;
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

.sold-out {
  color: red;
  font-weight: bold;
}

button {
  background-color: #4CAF50;
  color: #fff;
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

button:disabled {
  background-color: #ccc;
  cursor: not-allowed;
}
</style>