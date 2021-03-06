<!-- This example requires Tailwind CSS v2.0+ -->
<template>
  <div class="bg-white lg:border-t lg:border-b lg:border-gray-200">
    <nav class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8" aria-label="Progress">
      <ol
        class="
          rounded-md
          overflow-hidden
          lg:flex
          lg:border-l lg:border-r lg:border-gray-200
          lg:rounded-none
        "
      >
        <li
          v-for="(step, stepIdx) in steps"
          :key="step.id"
          class="relative overflow-hidden lg:flex-1"
        >
          <div
            :class="[
              stepIdx === 0 ? 'border-b-0 rounded-t-md' : '',
              stepIdx === steps.length - 1 ? 'border-t-0 rounded-b-md' : '',
              'border border-gray-200 overflow-hidden lg:border-0',
            ]"
          >
            <nuxt-link
              v-if="isActive(step.href)"
              :to="step.href"
              aria-current="step"
            >
              <span
                class="
                  absolute
                  top-0
                  left-0
                  w-1
                  h-full
                  bg-indigo-600
                  lg:w-full
                  lg:h-1
                  lg:bottom-0
                  lg:top-auto
                "
                aria-hidden="true"
              />
              <span
                :class="[
                  stepIdx !== 0 ? 'lg:pl-9' : '',
                  'px-6 py-5 flex items-start text-sm font-medium',
                ]"
              >
                <span class="flex-shrink-0">
                  <span
                    class="
                      w-10
                      h-10
                      flex
                      items-center
                      justify-center
                      border-2 border-indigo-600
                      rounded-full
                    "
                  >
                    <span class="text-indigo-600">{{ step.id }}</span>
                  </span>
                </span>
                <span class="mt-0.5 ml-4 min-w-0 flex flex-col">
                  <span
                    class="
                      text-xs
                      font-semibold
                      text-indigo-600
                      tracking-wide
                      uppercase
                    "
                    >{{ step.name }}</span
                  >
                  <span class="text-sm font-medium text-gray-500">{{
                    step.description
                  }}</span>
                </span>
              </span>
            </nuxt-link>
            <nuxt-link v-else :to="step.href" class="group">
              <span
                class="
                  absolute
                  top-0
                  left-0
                  w-1
                  h-full
                  bg-transparent
                  group-hover:bg-gray-200
                  lg:w-full
                  lg:h-1
                  lg:bottom-0
                  lg:top-auto
                "
                aria-hidden="true"
              />
              <span
                :class="[
                  stepIdx !== 0 ? 'lg:pl-9' : '',
                  'px-6 py-5 flex items-start text-sm font-medium',
                ]"
              >
                <span class="flex-shrink-0">
                  <span
                    class="
                      w-10
                      h-10
                      flex
                      items-center
                      justify-center
                      border-2 border-gray-300
                      rounded-full
                    "
                  >
                    <span class="text-gray-500">{{ step.id }}</span>
                  </span>
                </span>
                <span class="mt-0.5 ml-4 min-w-0 flex flex-col">
                  <span
                    class="
                      text-xs
                      font-semibold
                      text-gray-500
                      tracking-wide
                      uppercase
                    "
                    >{{ step.name }}</span
                  >
                  <span class="text-sm font-medium text-gray-500">{{
                    step.description
                  }}</span>
                </span>
              </span>
            </nuxt-link>
            <template v-if="stepIdx !== 0">
              <!-- Separator -->
              <div
                class="hidden absolute top-0 left-0 w-3 inset-0 lg:block"
                aria-hidden="true"
              >
                <svg
                  class="h-full w-full text-gray-300"
                  viewBox="0 0 12 82"
                  fill="none"
                  preserveAspectRatio="none"
                >
                  <path
                    d="M0.5 0V31L10.5 41L0.5 51V82"
                    stroke="currentcolor"
                    vector-effect="non-scaling-stroke"
                  />
                </svg>
              </div>
            </template>
          </div>
        </li>
      </ol>
    </nav>
  </div>
</template>

<script>
const steps = [
  {
    id: '01',
    name: 'Upload logo',
    description: 'Upload your company logo.',
    href: '/',
  },
  {
    id: '02',
    name: 'Update Details',
    description: 'Fill in your personal and contact details.',
    href: 'details',
  },
  {
    id: '03',
    name: 'Customize',
    description: 'Adjust the feel of the cards as you like',
    href: 'customize',
  },
  {
    id: '04',
    name: 'Download',
    description: 'Download your new business card',
    href: 'download',
  },
]

export default {
  data() {
    return {
      steps,
    }
  },
  methods: {
    isActive(path) {
      return this.$route.path.replace('/', '') == path.replace('/', '')
    },
  },
}
</script>