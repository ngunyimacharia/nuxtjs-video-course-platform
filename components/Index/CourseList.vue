<!-- This example requires Tailwind CSS v2.0+ -->
<template>
  <div class="bg-white overflow-hidden sm:rounded-md">
    <ul>
      <li v-for="(course, idx) in courses" :key="idx" class="m-5 shadow">
        <nuxt-link :to="`course/${course.slug}`" class="block hover:bg-gray-50">
          <div class="flex items-center px-4 py-4 sm:px-6">
            <div class="min-w-0 flex-1 flex items-center">
              <div class="flex-shrink-0">
                <cld-image
                  :public-id="course.image_public_id__cloudinary_"
                  :alt="course.title"
                  width="100"
                  height="100"
                  class="h-12 w-12 rounded-full"
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
                <div
                  class="
                    hidden
                    md:flex
                    flex-col
                    justify-center
                    text-sm text-gray-900
                  "
                >
                  <span>
                    Created on
                    {{ " " }}
                    <time :datetime="course.createdAt">{{
                      formatedDate(course.createdAt)
                    }}</time>
                  </span>
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
        </nuxt-link>
      </li>
    </ul>
  </div>
</template>

<script>
import { DateTime } from "luxon";

export default {
  data() {
    return {
      courses: [],
    };
  },
  async fetch() {
    console.log(this.$content("courses").fetch());
    this.courses = await this.$content("courses").fetch();
  },
  methods: {
    formatedDate(date) {
      return DateTime.fromISO(date).toLocaleString(DateTime.DATETIME_MED);
    },
  },
};
</script>