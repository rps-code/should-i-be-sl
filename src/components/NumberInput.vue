<template>
    <div>
        <label for="counter-input" class="block mb-1 text-sm font-medium text-white">{{ label }}</label>
        <div class="relative flex items-center">
            <button
                @click="decrement()"
                type="button"
                class="flex-shrink-0 bg-gray-700 hover:bg-gray-600 border-gray-600 inline-flex items-center justify-center border rounded-md h-5 w-5 focus:ring-gray-700 focus:ring-2 focus:outline-none"
            >
                <svg class="w-2.5 h-2.5 text-white" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 18 2">
                    <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M1 1h16" />
                </svg>
            </button>
            <input
                v-model="number"
                type="number"
                id="counter-input"
                class="flex-shrink-0 text-white border-0 bg-transparent text-sm font-normal focus:outline-none focus:ring-0 max-w-[2.5rem] text-center"
                placeholder=""
                required
                min="1"
                max="1000"
            />
            <button
                @click="increment()"
                type="button"
                class="flex-shrink-0 bg-gray-700 hover:bg-gray-600 border-gray-600 inline-flex items-center justify-center border rounded-md h-5 w-5 focus:ring-gray-700 focus:ring-2 focus:outline-none"
            >
                <svg class="w-2.5 h-2.5 text-white" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 18 18">
                    <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 1v16M1 9h16" />
                </svg>
            </button>
        </div>
        <p v-if="number === 69" class="absolute text-xs mt-1 text-gray-400">Nice.</p>
    </div>
</template>

<script setup lang="ts">
    import { ref, watch } from 'vue'

    defineProps<{
        label: string
    }>()

    const emit = defineEmits(['update:modelValue'])
    const number = ref(1)

    function increment() {
        if (number.value < 1000) number.value++
    }

    function decrement() {
        if (number.value > 1) number.value--
    }

    watch(number, (newValue, oldValue) => {
        let clampedValue = Math.max(1, Math.min(newValue, 1000))
        if (newValue !== clampedValue) {
            number.value = clampedValue
        }
        emit('update:modelValue', number.value)
    })
</script>
