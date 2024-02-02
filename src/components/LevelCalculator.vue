<template>
    <main class="mt-6">
        <div class="flex items-center justify-between mb-5">
            <NumberInput label="Your Level:" v-model="level" />
            <NumberInput label="Game Hours:" v-model="hours" />

            <div class="flex items-center">
                <input
                    v-model="mic"
                    id="default-checkbox"
                    type="checkbox"
                    value=""
                    class="w-4 h-4 rounded ring-offset-gray-800 bg-gray-700 border-gray-600"
                />
                <label for="default-checkbox" class="ms-2 text-sm font-medium text-gray-300">Do you use a mic?</label>
            </div>
        </div>

        <div v-if="messages.length">
            <p class="text-red-500 text-lg font-bold">You cannot be a SL as:</p>
            <ul class="text-white list-disc !pl-5">
                <li v-for="message in messages" :key="message">{{ message }}</li>
            </ul>
        </div>
        <div v-else class="text-green-500 text-lg font-bold">
            <p>You can be a SL!</p>
        </div>
    </main>
</template>

<script setup lang="ts">
    import { ref, computed } from 'vue'
    import NumberInput from '@/components/NumberInput.vue'

    const level = ref(1)
    const hours = ref(1)
    const mic = ref(false)

    const messages = computed(() => {
        const msgs = []

        if (!mic.value) msgs.push('You need to use your mic and communicate.')

        if (hours.value < 25) msgs.push('You need more game exposure.')

        if (level.value < 40) msgs.push('You need more in-game experience.')

        if (level.value > 60 && hours.value < 40) msgs.push('You should go back to Bob The Builder.')

        return msgs
    })
</script>
