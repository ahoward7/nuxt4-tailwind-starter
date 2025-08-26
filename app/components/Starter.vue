<template>
  <div :class="containerClass">
    <span :class="titleClass">
      Starter
      <span class="text-[#00C16A]">Nuxt 4</span>
      <span class="text-blue-500">TailwindCSS</span>
      App
    </span>
    <span :class="descClass">Click on a feature or recommendation to learn more!</span>
    <button
      class="w-fit cursor-pointer"
      :class="toggleBtnClass"
      @click="toggleColorMode"
    >
      <span v-if="isDark">🌙 Dark Mode (Click to switch to Light)</span>
      <span v-else>☀️ Light Mode (Click to switch to Dark)</span>
    </button>
    <div class="flex flex-col md:flex-row gap-8 w-full max-w-5xl justify-center items-stretch">
      <!-- Features Card -->
      <div class="flex-1 bg-gradient-to-br from-purple-500 to-blue-500 rounded-2xl shadow-xl p-8 flex flex-col">
        <h2 class="text-2xl font-bold mb-4 text-center text-white drop-shadow">
          Features
        </h2>
        <div class="flex flex-col gap-5 mb-2 text-lg text-white">
          <div>
            <span class="font-bold text-white">Dark Mode</span>
            <div class="text-white text-base font-normal">
              Toggle between light and dark themes using <NuxtLink to="https://color-mode.nuxtjs.org/" target="_blank" class="font-bold text-white underline">
                @nuxtjs/color-mode
              </NuxtLink>.
            </div>
          </div>
          <div>
            <NuxtLink to="https://nuxt.com" target="_blank" class="font-bold text-white hover:underline">
              Nuxt 4
            </NuxtLink>
            <div class="text-white text-base font-normal">
              Latest Nuxt for server-side rendering, static site generation, and hybrid apps.
            </div>
          </div>
          <div>
            <NuxtLink to="https://tailwindcss.com" target="_blank" class="font-bold text-white hover:underline">
              Tailwind CSS
            </NuxtLink>
            <div class="text-white text-base font-normal">
              Utility-first CSS framework for rapid UI development.
            </div>
          </div>
          <div>
            <NuxtLink to="https://www.typescriptlang.org/" target="_blank" class="font-bold text-white hover:underline">
              TypeScript
            </NuxtLink>
            <div class="text-white text-base font-normal">
              Type-safe development out of the box.
            </div>
          </div>
          <div>
            <NuxtLink to="https://eslint.org/" target="_blank" class="font-bold text-white hover:underline">
              ESLint
            </NuxtLink>
            <div class="text-white text-base font-normal">
              Lints and auto-fixes code for consistent style and to catch errors early.
            </div>
          </div>
          <div>
            <NuxtLink to="https://bun.sh/" target="_blank" class="font-bold text-white hover:underline">
              bun
            </NuxtLink>
            <NuxtLink to="https://www.npmjs.com/" target="_blank" class="font-bold text-white hover:underline ml-2">
              npm
            </NuxtLink>
            <NuxtLink to="https://pnpm.io/" target="_blank" class="font-bold text-white hover:underline ml-2">
              pnpm
            </NuxtLink>
            <NuxtLink to="https://yarnpkg.com/" target="_blank" class="font-bold text-white hover:underline ml-2">
              yarn
            </NuxtLink>
            <div class="text-white text-base font-normal">
              Flexible support for multiple package managers.
            </div>
          </div>
        </div>
      </div>
      <!-- Recommendations Card -->
      <div class="flex-1 bg-white rounded-2xl shadow-xl p-8 border-t-4 border-blue-500 flex flex-col">
        <h3 class="text-2xl font-semibold mb-4 text-center text-blue-500 drop-shadow">
          Recommended Additions
        </h3>
        <div class="flex flex-col gap-5 text-lg text-black">
          <div>
            <NuxtLink to="https://nuxt.com/modules/icon" target="_blank" class="font-bold text-blue-500 hover:underline">
              @nuxt/icon
            </NuxtLink>
            <div class="text-black text-base font-normal">
              Easily add SVG icons to your project with Nuxt integration.
            </div>
          </div>
          <div>
            <NuxtLink to="https://nuxt.com/modules/fonts" target="_blank" class="font-bold text-blue-500 hover:underline">
              @nuxt/fonts
            </NuxtLink>
            <div class="text-black text-base font-normal">
              Efficiently load and manage web fonts in your Nuxt app.
            </div>
          </div>
          <div>
            <NuxtLink to="https://nuxt.com/modules/test-utils" target="_blank" class="font-bold text-blue-500 hover:underline">
              @nuxt/test-utils
            </NuxtLink>
            <div class="text-black text-base font-normal">
              Utilities for unit and integration testing in Nuxt projects.
            </div>
          </div>
          <div>
            <NuxtLink to="https://nuxt.com/modules/auth-utils" target="_blank" class="font-bold text-blue-500 hover:underline">
              @nuxt/auth-utils
            </NuxtLink>
            <div class="text-black text-base font-normal">
              Helpers for authentication flows and testing auth logic in Nuxt apps.
            </div>
          </div>
          <div>
            <NuxtLink to="https://pinia.vuejs.org/ssr/nuxt.html" target="_blank" class="font-bold text-blue-500 hover:underline">
              @pinia/nuxt
            </NuxtLink>
            <div class="text-black text-base font-normal">
              Official state management solution for Vue and Nuxt.
            </div>
          </div>
          <div>
            <NuxtLink to="https://vueuse.org/" target="_blank" class="font-bold text-blue-500 hover:underline">
              @vueuse/core
            </NuxtLink>
            <div class="text-black text-base font-normal">
              Collection of essential Vue Composition API utilities.
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { useNuxtApp } from '#app'
import { computed, watch } from 'vue'
const nuxtApp = useNuxtApp()
const colorMode = useColorMode()

const isDark = computed(() => colorMode.value === 'dark')

const containerClass = computed(() => [
  'h-screen flex flex-col justify-center items-center pb-[10vh]',
  isDark.value
    ? 'bg-gradient-to-br from-gray-900 via-gray-800 to-gray-700 text-white'
    : 'bg-gradient-to-br from-green-100 via-purple-200 to-blue-300 text-black'
])

const titleClass = computed(() => [
  'flex gap-4 text-6xl mb-12 font-extrabold tracking-tight drop-shadow-lg',
  isDark.value ? 'text-white' : 'text-black'
])

const descClass = computed(() => [
  'mb-8 text-xl font-semibold',
  isDark.value ? 'text-white' : 'text-black'
])

const toggleBtnClass = computed(() => [
  'mb-8 px-4 py-2 rounded-lg font-semibold border border-blue-400',
  'bg-white text-blue-600 dark:text-blue-200',
  'hover:bg-blue-50 transition'
])

// SSR: set color mode from cookie
if (import.meta.server) {
  const cookie = nuxtApp.ssrContext?.event?.req?.headers.cookie || ''
  const match = cookie.match(/color_mode=(dark|light)/)
  if (match) {
    colorMode.preference = match[1] || ''
    colorMode.value = match[1] || ''
  }
}

// Client: keep color mode in sync with cookie
if (import.meta.client) {
  watch(
    () => colorMode.value,
    (v) => {
      document.cookie = `color_mode=${v}; path=/; SameSite=Lax`
    },
    { immediate: true }
  )
}

function toggleColorMode() {
  if (!colorMode) return
  colorMode.preference = colorMode.value === 'dark' ? 'light' : 'dark'
}
</script>
