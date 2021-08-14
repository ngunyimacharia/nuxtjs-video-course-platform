<template>
  <div>
    <div class="relative bg-white overflow-hidden">
      <div class="max-w-7xl mx-auto">
        <div
          class="
            relative
            z-10
            pb-8
            bg-white
            sm:pb-16
            md:pb-20
            lg:max-w-2xl
            lg:w-full
            lg:pb-28
            xl:pb-32
          "
        >
          <svg
            class="
              hidden
              lg:block
              absolute
              right-0
              inset-y-0
              h-full
              w-48
              text-white
              transform
              translate-x-1/2
            "
            fill="currentColor"
            viewBox="0 0 100 100"
            preserveAspectRatio="none"
            aria-hidden="true"
          >
            <polygon points="50,0 100,0 50,100 0,100" />
          </svg>

          <main
            class="
              mt-10
              mx-auto
              max-w-7xl
              px-4
              sm:mt-12
              sm:px-6
              md:mt-16
              lg:mt-20
              lg:px-8
              xl:mt-28
            "
          >
            <div class="sm:text-center lg:text-left">
              <h1
                class="
                  text-3xl
                  tracking-tight
                  font-extrabold
                  text-gray-900
                  sm:text-4xl
                  md:text-5xl
                "
              >
                <span class="block text-indigo-600 xl:inline">
                  {{ course.title }}
                </span>
              </h1>
              <p
                class="
                  my-6
                  text-base text-gray-500
                  sm:my-10
                  sm:text-lg
                  sm:max-w-xl
                  sm:mx-auto
                  md:my-10
                  md:text-xl
                  lg:mx-0
                "
              >
                {{ course.description }}
              </p>

              <nuxt-link to="/">
                <button
                  type="button"
                  class="
                    inline-flex
                    items-center
                    px-6
                    py-3
                    border border-transparent
                    text-base
                    font-medium
                    rounded-md
                    text-indigo-700
                    bg-indigo-100
                    hover:bg-indigo-200
                    focus:outline-none
                    focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500
                  "
                >
                  <svg
                    class="w-6 h-6"
                    fill="none"
                    stroke="currentColor"
                    viewBox="0 0 24 24"
                    xmlns="http://www.w3.org/2000/svg"
                  >
                    <path
                      stroke-linecap="round"
                      stroke-linejoin="round"
                      stroke-width="2"
                      d="M15 19l-7-7 7-7"
                    ></path>
                  </svg>
                  &nbsp; Back to Course List
                </button>
              </nuxt-link>
            </div>
          </main>
        </div>
      </div>
      <div class="lg:absolute lg:inset-y-0 lg:right-0 lg:w-1/2">
        <cld-image
          class="h-56 w-full object-cover sm:h-72 md:h-96 lg:w-full lg:h-full"
          :public-id="course.image_public_id__cloudinary_"
          alt=""
        />
      </div>
    </div>
    <ul
      role="list"
      class="
        m-10
        grid grid-cols-2
        gap-x-4 gap-y-8
        sm:grid-cols-3
        sm:gap-x-6
        lg:grid-cols-4
        xl:gap-x-8
      "
    >
      <li
        v-for="(lesson, index) in course.lessons"
        :key="index"
        class="relative"
      >
        <Lesson :lesson="lesson" />
      </li>
    </ul>
  </div>
</template>

<script>
import Lesson from "@/components/course/Lesson";

export default {
  components: {
    Lesson,
  },
  async asyncData({ $content, params }) {
    const course = await $content("courses", params.slug).fetch();

    console.log(course);

    return { course };
  },
  data() {
    return {};
  },
};
</script>