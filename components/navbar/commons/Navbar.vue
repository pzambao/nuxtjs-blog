<template>
  <header class="bg-gray-900 text-sm flex py-5 px-5 justify-between items-center sticky top-0 z-20 text-white">
    <NuxtLink to="/">
      <img
        src="https://nuxt.com/assets/design-kit/icon-green.svg"
        width="55"
        height="55"
        alt="Clica para voltar para o início"
      />
    </NuxtLink>
    <button class="p-1 md:hidden" @click="openMenu">
      <MenuIcon class="fill-white w-10 h-10" />
    </button>
    <nav class="hidden md:flex items-center gap-10 text-md">
      <NuxtLink to="/">
        Início
      </NuxtLink>
      <NuxtLink to="/search-cep/">
        BuscarCEP
      </NuxtLink>
    </nav>
    <NavbarMenu :is-visible="isMenuOpen" @closeMenu="closeMenu" />
  </header>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import NavbarMenu from './NavbarMenu.vue'
import MenuIcon from '@/components/navbar/icons/MenuIcon.vue'

const isMenuOpen = ref(false)

const openMenu = () => {
  isMenuOpen.value = true
}

const closeMenu = () => {
  isMenuOpen.value = false
}
</script>
