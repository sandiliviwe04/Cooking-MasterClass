<template>
  <div class="course-catalogue">
    <CourseCard
      v-for="course in courses"
      :key="course.id"
      :course="course"
      @add-to-wishlist="addToWishlist"
    />
  </div>
</template>

<script>
import CourseCard from './CourseCard.vue'
import { courses } from '../data.js'

export default {
  name: 'CourseCatalogue',
  components: { CourseCard },
  data() {
    return {
      courses
    }
  },
  methods: {
    addToWishlist(course) {
      this.$emit('add-to-wishlist', course)
    }
  }
}
</script>

<style scoped>
.course-catalogue {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
</style>