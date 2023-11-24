<script>
export default {
  data() {
    return {
      showOptions: false,
      modeValue: null,
      darkMode: null
    }
  },
  methods: {
    setDarkMode() {
      const theme = window.matchMedia('(prefers-color-scheme: dark)').matches ? 'dark' : 'light'
      if ((this.modeValue === null && theme === 'dark') || this.modeValue === 1) {
        this.darkMode = 1
      } else {
        this.darkMode = 0
      }
      this.$emit('setDarkMode', this.darkMode)
    }
  },
  mounted() {
    const storedTheme = localStorage.getItem('theme')
    if (storedTheme === 'dark') {
      this.darkMode = 1
    }
  }
}
</script>
<template>
  <div class="">
    <button
      class="group max-w-8 relative"
      @click="
        () => {
          this.showOptions = !this.showOptions
        }
      "
    >
      <span v-if="darkMode === 1"
        ><svg
          class="w-8 h-8 text-white"
          aria-hidden="true"
          xmlns="http://www.w3.org/2000/svg"
          fill="currentColor"
          viewBox="0 0 20 20"
        >
          <path
            d="M10 15a5 5 0 1 0 0-10 5 5 0 0 0 0 10Zm0-11a1 1 0 0 0 1-1V1a1 1 0 0 0-2 0v2a1 1 0 0 0 1 1Zm0 12a1 1 0 0 0-1 1v2a1 1 0 1 0 2 0v-2a1 1 0 0 0-1-1ZM4.343 5.757a1 1 0 0 0 1.414-1.414L4.343 2.929a1 1 0 0 0-1.414 1.414l1.414 1.414Zm11.314 8.486a1 1 0 0 0-1.414 1.414l1.414 1.414a1 1 0 0 0 1.414-1.414l-1.414-1.414ZM4 10a1 1 0 0 0-1-1H1a1 1 0 0 0 0 2h2a1 1 0 0 0 1-1Zm15-1h-2a1 1 0 1 0 0 2h2a1 1 0 0 0 0-2ZM4.343 14.243l-1.414 1.414a1 1 0 1 0 1.414 1.414l1.414-1.414a1 1 0 0 0-1.414-1.414ZM14.95 6.05a1 1 0 0 0 .707-.293l1.414-1.414a1 1 0 1 0-1.414-1.414l-1.414 1.414a1 1 0 0 0 .707 1.707Z"
          />
        </svg>
      </span>

      <span v-else
        ><svg
          class="w-6 h-8 text-gray-500"
          aria-hidden="true"
          xmlns="http://www.w3.org/2000/svg"
          fill="currentColor"
          viewBox="0 0 18 20"
        >
          <path
            d="M17.8 13.75a1 1 0 0 0-.859-.5A7.488 7.488 0 0 1 10.52 2a1 1 0 0 0 0-.969A1.035 1.035 0 0 0 9.687.5h-.113a9.5 9.5 0 1 0 8.222 14.247 1 1 0 0 0 .004-.997Z"
          />
        </svg>
      </span>
    </button>

    <div
      v-if="showOptions"
      class="absolute flex justify-items-start mt-2 px-2 w-32 right-0 mr-4 rounded-md shadow-lg bg-slate-100 dark:bg-black"
    >
      <div class="py-1">
        <button
          class="block pl-4 py-2 text-sm text-gray-700"
          @click="
            () => {
              this.modeValue = 0
              this.setDarkMode()
              this.showOptions = !this.showOptions
            }
          "
        >
          <span class="flex"
            ><svg
              class="w-4 h-4 text-gray-800 dark:text-white mr-2"
              aria-hidden="true"
              xmlns="http://www.w3.org/2000/svg"
              fill="currentColor"
              viewBox="0 0 20 20"
            >
              <path
                d="M10 15a5 5 0 1 0 0-10 5 5 0 0 0 0 10Zm0-11a1 1 0 0 0 1-1V1a1 1 0 0 0-2 0v2a1 1 0 0 0 1 1Zm0 12a1 1 0 0 0-1 1v2a1 1 0 1 0 2 0v-2a1 1 0 0 0-1-1ZM4.343 5.757a1 1 0 0 0 1.414-1.414L4.343 2.929a1 1 0 0 0-1.414 1.414l1.414 1.414Zm11.314 8.486a1 1 0 0 0-1.414 1.414l1.414 1.414a1 1 0 0 0 1.414-1.414l-1.414-1.414ZM4 10a1 1 0 0 0-1-1H1a1 1 0 0 0 0 2h2a1 1 0 0 0 1-1Zm15-1h-2a1 1 0 1 0 0 2h2a1 1 0 0 0 0-2ZM4.343 14.243l-1.414 1.414a1 1 0 1 0 1.414 1.414l1.414-1.414a1 1 0 0 0-1.414-1.414ZM14.95 6.05a1 1 0 0 0 .707-.293l1.414-1.414a1 1 0 1 0-1.414-1.414l-1.414 1.414a1 1 0 0 0 .707 1.707Z"
              />
            </svg>
            <p class="dark:text-white">Light</p>
          </span>
        </button>
        <button
          class="block pl-4 py-2 text-sm text-gray-700"
          @click="
            () => {
              this.modeValue = 1
              this.setDarkMode()
              this.showOptions = !this.showOptions
            }
          "
        >
          <span class="flex">
            <svg
              class="w-4 h-4 text-gray-800 dark:text-white mr-2"
              aria-hidden="true"
              xmlns="http://www.w3.org/2000/svg"
              fill="currentColor"
              viewBox="0 0 18 20"
            >
              <path
                d="M17.8 13.75a1 1 0 0 0-.859-.5A7.488 7.488 0 0 1 10.52 2a1 1 0 0 0 0-.969A1.035 1.035 0 0 0 9.687.5h-.113a9.5 9.5 0 1 0 8.222 14.247 1 1 0 0 0 .004-.997Z"
              />
            </svg>
            <p class="dark:text-white">Dark</p>
          </span>
        </button>
        <button
          class="block pl-4 py-2 text-sm text-gray-700"
          @click="
            () => {
              this.modeValue = null
              this.setDarkMode()
              this.showOptions = !this.showOptions
            }
          "
        >
          <span class="flex">
            <svg
              class="w-4 h-4 text-gray-800 dark:text-white mr-2"
              aria-hidden="true"
              xmlns="http://www.w3.org/2000/svg"
              fill="currentColor"
              viewBox="0 0 20 20"
            >
              <path
                d="M20 9V2a2 2 0 0 0-2-2H2a2 2 0 0 0-2 2v7h20ZM0 11v2a2 2 0 0 0 2 2h7v3H6a1 1 0 0 0 0 2h8a1 1 0 0 0 0-2h-3v-3h7a2 2 0 0 0 2-2v-2H0Z"
              />
            </svg>
            <p class="dark:text-white">System</p>
          </span>
        </button>
      </div>
    </div>
  </div>
</template>
