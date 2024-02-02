<template>
    <main class="block max-w-xl p-6 rounded-lg shadow bg-slate-800">
        <GitHub />

        <h5 class="mb-2 text-2xl font-bold tracking-tight text-white">Should I Be SL? 🤔</h5>
        <p class="font-normal text-gray-400">A simple tool to advise you on if you should be Squad Leader in HLL.</p>

        <LevelCalculator />

        <p class="mt-5 text-sm text-right text-gray-500">
            <a href="https://discordapp.com/users/292432182557933588/">Created with ❤️ by <span class="underline">rps</span></a>
        </p>
    </main>
</template>

<script setup lang="ts">
    import GitHub from '@/components/GitHub.vue'
    import LevelCalculator from '@/components/LevelCalculator.vue'
</script>
