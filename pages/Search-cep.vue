<template>
  <div class="items-center justify-center bg-gray-900 h-screen w-full pb-8">
    <Navbar />
    <form class="grid grid-cols-1 gap-4 w-[70%] sm:w-[30%] pt-4 justify-self-center text-white " @submit.prevent="handleSubmit">
      <div>
        <label for="cep" class="block text-sm font-medium text-left mb-1">CEP</label>
        <input
          v-model="form.cep"
          class="w-full bg-transparent border-b border-white focus:outline-none focus:border-white text-white"
          type="text"
          @input="checkCep"
        />
        <span v-if="errors.cep">CEP é obrigatório e deve ter 8 caracteres</span>
      </div>

      <div>
        <label for="uf" class="block text-sm font-medium text-left mb-1">Estado</label>
        <input
          v-model="form.uf"
          type="text"
          class="w-full bg-transparent border-b border-white focus:outline-none focus:border-white text-white"
        />
        <span v-if="errors.uf">Estado é obrigatório</span>
      </div>

      <div>
        <label for="localidade" class="block text-sm font-medium text-left mb-1">Cidade</label>
        <input
          v-model="form.localidade"
          type="text"
          class="w-full bg-transparent border-b border-white focus:outline-none focus:border-white text-white"
        />
        <span v-if="errors.localidade">Cidade é obrigatória</span>
      </div>

      <div>
        <label for="bairro" class="block text-sm font-medium text-left mb-1">Bairro</label>
        <input
          v-model="form.bairro"
          type="text"
          class="w-full bg-transparent border-b border-white focus:outline-none focus:border-white text-white"
        />
        <span v-if="errors.bairro">Bairro é obrigatório</span>
      </div>

      <div>
        <label for="logradouro" class="block text-sm font-medium text-left mb-1">Rua</label>
        <input
          v-model="form.logradouro"
          type="text"
          class="w-full bg-transparent border-b border-white focus:outline-none focus:border-white text-white"
        />
        <span v-if="errors.logradouro">Rua é obrigatória</span>
      </div>

      <div>
        <label for="number" class="block text-sm font-medium text-left mb-1">Número</label>
        <input
          v-model="form.number"
          type="text"
          class="w-full bg-transparent border-b border-white focus:outline-none focus:border-white text-white"
        />
        <span v-if="errors.number">Número é obrigatório</span>
      </div>

      <div>
        <label for="complement" class="block text-sm font-medium text-left mb-1">Complemento</label>
        <input
          v-model="form.complement"
          type="text"
          class="w-full bg-transparent border-b border-white focus:outline-none focus:border-white text-white"
        />
      </div>

      <div class="text-right">
        <button type="submit" class="bg-white text-black p-1 border-b rounded-sm ">
          Enviar
        </button>
      </div>
    </form>
    <Footer />
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import axios from 'axios'
import Swal from 'sweetalert2'

interface CepValues {
  cep: string;
  uf: string;
  localidade: string;
  bairro: string;
  logradouro: string;
  number: string;
  complement: string;
}

const form = ref<CepValues>({
  cep: '',
  uf: '',
  localidade: '',
  bairro: '',
  logradouro: '',
  number: '',
  complement: ''
})

const errors = ref({
  cep: false,
  uf: false,
  localidade: false,
  bairro: false,
  logradouro: false,
  number: false
})

const fetchCepData = async (cep: string) => {
  try {
    const response = await axios.get(`https://viacep.com.br/ws/${cep}/json/`)
    const data = response.data
    form.value.uf = data.uf || ''
    form.value.localidade = data.localidade || ''
    form.value.bairro = data.bairro || ''
    form.value.logradouro = data.logradouro || ''
  } catch (error) {
    // eslint-disable-next-line no-console
    console.error('Erro ao buscar o CEP:', error)
  }
}

const checkCep = () => {
  if (form.value.cep.length === 8) {
    fetchCepData(form.value.cep)
  }
}

const handleSubmit = () => {
  errors.value.cep = form.value.cep.length !== 8
  errors.value.uf = !form.value.uf
  errors.value.localidade = !form.value.localidade
  errors.value.bairro = !form.value.bairro
  errors.value.logradouro = !form.value.logradouro
  errors.value.number = !form.value.number

  const hasErrors = Object.values(errors.value).some(error => error)

  if (!hasErrors) {
    Swal.fire({
      title: 'Sucesso!',
      text: 'Endereço validado com sucesso!',
      icon: 'success',
      confirmButtonText: 'Ok'
    })
    // eslint-disable-next-line no-console
    console.log(form.value)
  }
}
</script>

<style lang="scss" scoped>
html, body{
  background-color: #111827;
}
</style>