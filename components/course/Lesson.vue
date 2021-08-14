<template>
  <div class="relative">
    <div
      class="
        relative
        group
        block
        w-full
        aspect-w-10 aspect-h-7
        rounded-lg
        bg-gray-100
        focus-within:ring-2
        focus-within:ring-offset-2
        focus-within:ring-offset-gray-100
        focus-within:ring-indigo-500
        overflow-hidden
      "
    >
      <cld-video
        :public-id="lesson.video_public_id__cloudinary_"
        alt=""
        class="object-cover pointer-events-none group-hover:opacity-75"
      />
      <button
        type="button"
        class="absolute h-full w-full inset-0 focus:outline-none text-gray-100"
      >
        <svg
          class="w-10 h-10 m-auto"
          fill="none"
          stroke="currentColor"
          viewBox="0 0 24 24"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M14.752 11.168l-3.197-2.132A1 1 0 0010 9.87v4.263a1 1 0 001.555.832l3.197-2.132a1 1 0 000-1.664z"
          ></path>
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M21 12a9 9 0 11-18 0 9 9 0 0118 0z"
          ></path>
        </svg>
      </button>
    </div>
    <p
      class="my-5 block font-medium text-gray-900 truncate pointer-events-none"
    >
      {{ lesson.title }}
    </p>
    <p class="block text-sm font-medium text-gray-500 pointer-events-none">
      {{ lesson.description }}
    </p>
  </div>
</template>

<script>
export default {
  props: {
    lesson: {
      required: true,
      type: Object,
    },
  },
};
</script>