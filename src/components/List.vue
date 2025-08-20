<script setup>
import { ref } from 'vue'
const props = defineProps({
    title: String,
    id: Number,
    count: Number
})
const emit = defineEmits(["openModal"])
const isExpanded = ref(true)
const toggleList = () => {
    if (isExpanded.value) {
        isExpanded.value = false
    } else {
        isExpanded.value = true
    }
}
</script>

<template>
    <div class="p-3 rounded-lg min-w-[250px] flex flex-col transition-all ease-in-out duration-300 border" :class="{
        'border-amber-700': id === 1,
        'border-blue-700': id === 2,
        'border-green-700': id === 3,
        'border-slate-700': id === 4
    }
        ">
        <h2 class="font-medium cursor-pointer select-none font-semibold" :class="{
            'text-amber-700': id === 1,
            'text-blue-700': id === 2,
            'text-green-700': id === 3,
            'text-slate-700': id === 4
        }" @click="toggleList">{{ title }}</h2>
        <div class="mt-3 mb-1 border-t border-b pb-3 pt-2" :class="{
            'border-amber-700': id === 1,
            'border-blue-700': id === 2,
            'border-green-700': id === 3,
            'border-slate-700': id === 4
        }
            " v-if="isExpanded">
            <div v-if="count > 0">
                <slot />
            </div>
            <div v-else class="text-sm" :class="{
                'text-amber-700/40': id === 1,
                'text-blue-700/40': id === 2,
                'text-green-700/40': id === 3,
                'text-slate-700/40': id === 4
            }
                ">
                <slot />
                No cards added yet
            </div>
        </div>
        <button
            class="w-ful p-2  mt-2 text-sm font-medium rounded text-white text-center border"
            :class="{
                'bg-amber-700 border-amber-700 hover:border-amber-700 hover:text-amber-700 hover:bg-white': id === 1,
                'bg-blue-700 border-blue-700 hover:border-blue-700 hover:text-blue-700 hover:bg-white': id === 2,
                'bg-green-700 border-green-700 hover:border-green-700 hover:text-green-700 hover:bg-white': id === 3,
                'bg-slate-700 border-slate-700 hover:border-slate-700 hover:text-slate-700 hover:bg-white': id === 4
            }
                " v-if="id < 4" @click="emit('openModal', id)">+ Add Card</button>
    </div>
</template>