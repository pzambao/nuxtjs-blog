<template>
  <div class="bg-gray-900 h-screen text-white ">
    <Navbar />
    <div class="flex justify-center flex-col items-center h-[75%] px-3">
      <h1 class="mb-4 text-xl text-center">
        <b>Projeto para estudos:</b>
      </h1>
      <p class="text-center">
        Formulário para busca de endereço através do cep utilizando <b>NuxtJS</b>, <b>Typescript</b> e <b>TailwindCSS</b>
      </p>
      <NuxtLink to="/search-cep/" class="bg-gray-300 hover:bg-gray-400 text-gray-800 font-bold mt-8 py-1 px-4 rounded inline-flex items-center">
        <span>Acessar Formulário</span>
      </NuxtLink>
    </div>
    <Footer />
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  name: 'IndexPage',
  head () {
    return {
      title: 'Início | NuxtJS Form',
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'Validação de CEP para estudos utilizando NuxtJS, Typescript e Tailwindcss'
        }
      ]
    }
  }
})
</script>

<style>
html, body{
  background-color: #111827;
}
</style>
