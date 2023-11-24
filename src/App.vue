<script>
import DarkModeButton from '@/components/DarkModeButton.vue'
export default {
  data() {
    return {
      modeValue: null,
      isDarkMode: false,
      //propValue: null
    }
  },
  components: { DarkModeButton },
  methods: {
    setDarkMode(modeValue) {
      this.modeValue = modeValue
      if (this.modeValue === 0) {
        this.isDarkMode = false
        this.applyTheme(this.isDarkMode)
      } else {
        this.isDarkMode = true
        this.applyTheme(this.isDarkMode)
      }
    },

    applyTheme(pickedTheme) {
      if (pickedTheme) {
        document.documentElement.classList.add('dark')
        localStorage.setItem('theme', 'dark')
      } else {
        document.documentElement.classList.remove('dark')
        localStorage.setItem('theme', 'ligth')
      }
    },

    themeDetection() {
      const storedTheme = localStorage.getItem('theme')
      if (storedTheme === 'dark') {
        return true
      } else {
        return false
      }
    }
  },
  mounted() {
    this.isDarkMode = this.themeDetection()
    this.applyTheme(this.isDarkMode)
  }
}
</script>

<template>
  <div class="bg-white dark:bg-slate-900 h-screen w-screen flex justify-end pt-5 pr-8">
    <DarkModeButton @setDarkMode="setDarkMode" />
  </div>
</template>
