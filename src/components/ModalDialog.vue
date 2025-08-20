<script setup>
import { ref } from 'vue'
const props = defineProps({
    isOpen: {
        type: Boolean,
        default: false
    },
    currentList: {
        type: Number,
        required: true
    }
})
const emit = defineEmits(["closeModal", "addCard"])
const title = ref("")
const description = ref("")
const handleSubmit = () => {
    emit('addCard', title.value, description.value)
    title.value = ''
    description.value = ''
}
</script>

<template>
    <div v-if="isOpen" role="dialog" aria-modal="true"
        class="fixed top-1/2 left-1/2 -translate-1/2 bg-black/50 w-full h-full z-20">
        <div class="absolute top-1/2 left-1/2 -translate-1/2 bg-white p-4 rounded max-w-md w-full">
            <h3 class="text-md font-semibold mb-4 pb-4 border-b border-slate-100" :class="{
                'text-amber-700': currentList === 1,
                'text-blue-700': currentList === 2,
                'text-green-700': currentList === 3,
                'text-slate-700': currentList === 4
            }">Add New Card</h3>
            <button class="absolute top-4 right-6 cursor-pointer" :class="{
                'text-amber-700': currentList === 1,
                'text-blue-700': currentList === 2,
                'text-green-700': currentList === 3,
                'text-slate-700': currentList === 4
            }" @click="emit('closeModal')">X</button>
            <form @submit.prevent="handleSubmit()">
                <input :class="{
                    'border-amber-800/40 placeholder:text-amber-800/40': currentList === 1,
                    'border-blue-800/40 placeholder:text-blue-800/40': currentList === 2,
                    'border-green-800/40 placeholder:text-green-800/40': currentList === 3,
                    'border-slate-800/40 placeholder:text-slate-800/40': currentList === 4,
                }
                    " required type="text" placeholder="Card title" aria-label="Card title"
                    class="w-full p-2 mb-4 border rounded " v-model="title">
                <textarea :class="{
                    'border-amber-800/40 placeholder:text-amber-800/40': currentList === 1,
                    'border-blue-800/40 placeholder:text-blue-800/40': currentList === 2,
                    'border-green-800/40 placeholder:text-green-800/40': currentList === 3,
                    'border-slate-800/40 placeholder:text-slate-800/40': currentList === 4,
                }
                    " required placeholder="Card desciption" aria-label="Card desciption"
                    class="w-full p-2 mb-4 border rounded " v-model="description"></textarea>
                <div class="flex justify-end gap-2">

                    <button :class="{
                        'bg-amber-700 border-amber-700 hover:border-amber-700 hover:text-amber-700 hover:bg-white': currentList === 1,
                        'bg-blue-700 border-blue-700 hover:border-blue-700 hover:text-blue-700 hover:bg-white': currentList === 2,
                        'bg-green-700 border-green-700 hover:border-green-700 hover:text-green-700 hover:bg-white': currentList === 3,
                        'bg-slate-700 border-slate-700 hover:border-slate-700 hover:text-slate-700 hover:bg-white': currentList === 4
                    }
                        " type="submit" class="border px-4 py-2 rounded text-white w-full">Save</button>
                </div>
            </form>
        </div>
    </div>
</template>