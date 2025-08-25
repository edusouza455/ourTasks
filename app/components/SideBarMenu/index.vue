<template>
  <button
    v-if="!menuOpen"
    @click="menuOpen = true"
    class="p-2 fixed top-4 left-4 bg-stone-200 rounded shadow transition-transform duration-200 hover:scale-110"
  >
    <Icon name="pixelarticons:menu" class="w-5 h-5 text-black" />
  </button>

  <div v-if="menuOpen" class="flex flex-col h-full p-3 w-60 min-h-screen shadow-xl bg-stone-50">
    <div class="flex items-center justify-between">
      <h2>Quadro de Tarefas</h2>
      <button @click="menuOpen = !menuOpen" class="p-2">
        <Icon
          name="pixelarticons:menu"
          class="w-5 h-5 md:w-5 md:h-5 text-black transition-transform duration-200 hover:scale-110"
        />
      </button>
    </div>

    <div class="flex-1">
      <ul class="pt-10 pb-4 space-y-2 text-sm">
        <li class="rounded-sm">
          <button
            @click="exp = !exp"
            class="flex items-center p-2 space-x-3 rounded-md transition-transform duration-200 hover:scale-110"
          >
            <Icon
              name="pixelarticons:chart"
              class="w-5 h-5 md:w-5 md:h-5 text-black transition-transform duration-200 hover:scale-110"
            />
            <span>Tarefas</span>
          </button>

          <ul v-if="exp" class="pl-8 pt-2 space-y-1">
            <button @click="showModal = true" class="flex flex-row transition-transform duration-200 hover:scale-110">
              <Icon
                name="pixelarticons:plus"
                class="w-5 h-5 mr-2 md:w-5 md:h-5 text-black transition-transform duration-200 hover:scale-110"
              />
              <span>Nova Tarefa</span>
            </button>
          </ul>
        </li>

        <li class="rounded-sm transition-transform duration-200 hover:scale-110">
          <a rel="noopener noreferrer" href="#" class="flex items-center p-2 space-x-3 rounded-md">
            <Icon
              name="pixelarticons:card"
              class="w-5 h-5 md:w-5 md:h-5 text-black transition-transform duration-200 hover:scale-110"
            />
            <span>Quadro em Branco</span>
          </a>
        </li>
      </ul>
    </div>

    <div class="flex items-center p-2 mt-12 space-x-4 justify-self-end transition-transform duration-200 hover:scale-110">
      <NuxtImg src="/logoIcon.png" alt="gato" class="w-12 h-12 rounded-lg" />
      <div>
        <h2 class="text-sm font-semibold">Desenvolvido Por:</h2>
        <span class="flex items-center space-x-1">
          <a rel="noopener noreferrer" href="#" class="text-xs hover:underline dark:text-gray-600">Eduardo Souza</a>
        </span>
      </div>
    </div>
  </div>

  <Teleport to="body">
    <div
      v-if="showModal"
      class="fixed inset-0 z-[1000] flex items-center justify-center"
      role="dialog"
      aria-modal="true"
    >
     
      <div class="absolute inset-0 bg-black/50" @click="closeModal"></div>

      
      <div class="relative z-[1001] w-full max-w-md rounded-xl bg-white p-5 shadow-xl">
       
        <div class="mb-3 flex items-center justify-between">
          <h3 class="text-lg font-semibold">Nova Tarefa</h3>
          <button class="p-1 rounded hover:bg-stone-100" @click="closeModal" aria-label="Fechar modal">
            <Icon name="pixelarticons:close" class="w-4 h-4" />
          </button>
        </div>

        
        <form @submit.prevent="createTask" class="space-y-3">
          <div>
            <label class="mb-1 block text-sm font-medium">Título</label>
            <input
              v-model="newTitle"
              type="text"
              placeholder="Ex.: Implementar modal"
              class="w-full rounded border px-3 py-2"
              required
              autofocus
            />
          </div>

          <div>
            <label class="mb-1 block text-sm font-medium">Descrição</label>
            <textarea
              v-model="newDesc"
              rows="3"
              placeholder="Detalhes (opcional)"
              class="w-full rounded border px-3 py-2"
            ></textarea>
          </div>

        
          <div class="pt-2 flex justify-end gap-2">
            <button type="button" class="px-3 py-2 rounded border hover:bg-stone-50" @click="closeModal">Cancelar</button>
            <button type="submit" class="px-3 py-2 rounded bg-blue-600 text-white hover:bg-blue-700">Salvar</button>
          </div>
        </form>
      </div>
    </div>
  </Teleport>
</template>

<script setup>
import { ref } from 'vue'

const exp = ref(false)
const menuOpen = ref(false)
const showModal = ref(false)


const newTitle = ref('')
const newDesc = ref('')

function closeModal() {
  showModal.value = false
  newTitle.value = ''
  newDesc.value = ''
}

function createTask() {
	console.log(newTitle)
	console.log(newDesc)
  closeModal()
}
</script>

<style scoped>
</style>
