<template>
  <div>
    <Hero />
    <CourseList :courses="courses" />
  </div>
</template>

<script>
import Hero from "@/components/Index/Hero";
import CourseList from "@/components/Index/CourseList";

export default {
  components: {
    Hero,
    CourseList,
  },
  async asyncData({ $content }) {
    const courses = await $content("courses").fetch();

    return { courses };
  },
};
</script>
