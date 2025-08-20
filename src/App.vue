<script setup>
import Card from '@/components/Card.vue'
import List from '@/components/List.vue'
import { reactive, ref, watch } from 'vue';
import Draggable from 'vuedraggable';
import ModalDialog from './components/ModalDialog.vue';

const saved = localStorage.getItem('lists')
const lists = reactive(saved ? JSON.parse(saved) : [
  {
    id: 1,
    title: 'To Do',
    cards: []
  },
  {
    id: 2,
    title: 'In Progress',
    cards: []
  },
  {
    id: 3,
    title: 'Done',
    cards: []
  },
  {
    id: 4,
    title: 'Archived',
    cards: []
  }
])
watch(() => lists, (newVal) => {
  localStorage.setItem("lists", JSON.stringify(newVal))
}, { deep: true })

const isModalOpen = ref(false)
const currentList = ref(null)
const openModal = (list) => {
  currentList.value = list
  isModalOpen.value = true
}
const closeModal = () => {
  isModalOpen.value = false
}
const addCard = (title, description) => {
  const list = lists.find(list => list.id === currentList.value)
  if (!list) return
  list.cards.push({
    id: Date.now(),
    title: title,
    description: description
  })
  closeModal()
}
</script>

<template>
  <main class="p-5 font-sans">
    <div class="flex gap-5 py-5 overflow-x-auto">
      <div v-for="list in lists" :key="list.id">
        <List :title="list.title" :id="list.id" :count="list.cards.length" @openModal="openModal">
          <Draggable :list="list.cards" group="cards" item-key="id">
            <template #item="{ element }">
              <Card :list="list.id" :title="element.title" :description="element.description" />
            </template>
          </Draggable>
        </List>
      </div>
      <ModalDialog :is-open="isModalOpen" :currentList="currentList" @closeModal="closeModal" @addCard="addCard" />
    </div>
  </main>
</template>