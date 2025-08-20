<script setup>
const props = defineProps({
    title: String,
    description: String,
    list: Number
})
</script>

<template>
    <div class="bg-white p-2 my-2 rounded border cursor-pointer" :class="{
            'border-amber-600 text-amber-600': list === 1,
            'border-blue-600 text-blue-600': list === 2,
            'border-green-600 text-green-600': list === 3,
            'border-slate-600 text-slate-600': list === 4
        }
            ">
        <span class="text-sm font-medium">{{ title }}</span>
        <p class="text-xs text-gray-400">
            {{ description }}
        </p>
    </div>
</template>