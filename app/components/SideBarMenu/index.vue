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
					<Icon name="pixelarticons:menu"
          class="w-5 h-5 md:w-5 md:h-5 text-black transition-transform duration-200 hover:scale-110" />
				</button>
			</div>

			<div class="flex-1">
				<ul class="pt-10 pb-4 space-y-2 text-sm">
					<li class="rounded-sm">

						<button @click="exp = !exp" rel="noopener noreferrer" href="#" class="flex items-center p-2 space-x-3 rounded-md transition-transform duration-200 hover:scale-110">
							<Icon name="pixelarticons:chart"
              class="w-5 h-5 md:w-5 md:h-5 text-black transition-transform duration-200 hover:scale-110" />
							<span>Tarefas</span>
            </button >

            <ul v-if="exp" class="pl-8 pt-2 space-y-1">
              <button @click="showModal = true" class="flex flex-row transition-transform duration-200 hover:scale-110">
                <Icon name="pixelarticons:plus"
                class="w-5 h-5 mr-2 md:w-5 md:h-5 text-black transition-transform duration-200 hover:scale-110" />
                <span>Nova Tarefa</span>                
              </button>

              <Teleport to="body">
                <modal :show="showModal" @close="showModal = false">
                  <template #header>
                    <h3>Custom H</h3>
                  </template>
                </modal>

              </Teleport>

            </ul>

					</li>

          <li class="rounded-sm transition-transform duration-200 hover:scale-110">
						<a rel="noopener noreferrer" href="#" class="flex items-center p-2 space-x-3 rounded-md">
							<Icon name="pixelarticons:card"
              class="w-5 h-5 md:w-5 md:h-5 text-black transition-transform duration-200 hover:scale-110" />
							<span>Quadro em Branco</span>
						</a>
					</li>

				</ul>
			</div>
		<div class="flex items-center p-2 mt-12 space-x-4 justify-self-end transition-transform duration-200 hover:scale-110">
			<NuxtImg 
      src="/logoIcon.png" 
      alt="gato" 
      class="w-12 h-12 rounded-lg"/>
			<div>
				<h2 class="text-sm font-semibold">Desenvolvido Por:</h2>
				<span class="flex items-center space-x-1">
					<a rel="noopener noreferrer" href="#" class="text-xs hover:underline dark:text-gray-600">Eduardo Souza</a>
				</span>
			</div>
		</div>
	</div>
</template>

<script setup>
import { ref } from 'vue'


  const exp = ref(false)

  const menuOpen = ref(false)

  const showModal = ref(false)
 
 
</script>

<style scoped>

</style>