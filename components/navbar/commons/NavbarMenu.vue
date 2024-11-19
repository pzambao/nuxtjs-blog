<template>
  <div
    :class="[
      isVisible ? 'flex' : 'invisible',
      'fixed inset-0 w-full h-full bg-black bg-opacity-40 backdrop-blur-sm md:hidden text-white'
    ]"
  >
    <div class="w-full h-full bg-h-blue-900 shadow-md py-4 px-5">
      <div class="flex justify-between mb-5">
        <NuxtLink to="/" @click="handleClose">
          <img
            src="https://nuxt.com/assets/design-kit/icon-green.svg"
            width="55"
            height="55"
            alt=""
          />
        </NuxtLink>
        <button @click="handleClose">
          <MenuCloseIcon class="fill-white w-10 h-10" />
        </button>
      </div>
      <nav class="flex flex-col gap-5 text-xl p-5 items-center">
        <NuxtLink to="/" @click="handleClose">
          Início
        </NuxtLink>
        <NuxtLink to="/search-cep/" @click="handleClose">
          Buscar CEP
        </NuxtLink>
      </nav>
    </div>
  </div>
</template>

<script setup lang="ts">
import { defineProps, defineEmits } from 'vue'
import MenuCloseIcon from '@/components/navbar/icons/MenuCloseIcon.vue'

const props = defineProps({
  isVisible: {
    type: Boolean,
    required: true
  }
})

const emit = defineEmits(['closeMenu'])

const handleClose = () => {
  emit('closeMenu')
}
</script>
