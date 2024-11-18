<template>
  <div class="bg-gray-900 h-screen text-white ">
    <Navbar />
    <Head>
      <title>Início | NextJS Form</title>
      <meta name="description" content="Validação de CEP para estudos utilizando NextJS, Typescript e Tailwindcss" />
    </Head>
    <div class="flex justify-center flex-col items-center h-[75%] px-3">
      <h1 class="mb-4 text-xl text-center">
        <b>Projeto para estudos:</b>
      </h1>
      <p class="text-center">
        Formulário para busca de endereço através do cep utilizando <b>NuxtJS</b>, <b>Typescript</b> e <b>TailwindCSS</b>
      </p>
    </div>
    <Footer />
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  name: 'StorePage'
})
</script>
