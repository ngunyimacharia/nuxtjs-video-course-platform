<!-- This example requires Tailwind CSS v2.0+ -->
<template>
  <div class="bg-white overflow-hidden sm:rounded-md">
    <ul>
      <li v-for="(course, idx) in courses" :key="idx" class="m-5 shadow">
        <a href="" class="block hover:bg-gray-50">
          <div class="flex items-center px-4 py-4 sm:px-6">
            <div class="min-w-0 flex-1 flex items-center">
              <div class="flex-shrink-0">
                <img
                  class="h-12 w-12 rounded-full"
                  :src="course.image"
                  alt=""
                />
              </div>
              <div class="min-w-0 flex-1 px-4 md:grid md:grid-cols-2 md:gap-4">
                <div>
                  <p class="text-sm font-medium text-indigo-600 truncate">
                    {{ course.title }}
                  </p>
                  <p class="mt-2 flex items-center text-sm text-gray-500">
                    {{ course.description }}
                  </p>
                </div>
                <div class="hidden md:block">
                  <div>
                    <p class="text-sm text-gray-900">
                      Created on
                      {{ " " }}
                      <time :datetime="course.createdAt">{{
                        course.createdAt
                      }}</time>
                    </p>
                  </div>
                </div>
              </div>
            </div>
            <div>
              <svg
                class="w-4 h-4"
                fill="none"
                stroke="currentColor"
                viewBox="0 0 24 24"
                xmlns="http://www.w3.org/2000/svg"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M9 5l7 7-7 7"
                ></path>
              </svg>
            </div>
          </div>
        </a>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      courses: [],
    };
  },
  async fetch() {
    this.courses = await this.$content("courses").fetch();
  },
};
</script>