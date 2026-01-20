<template>
    <footer class="bg-slate-950 text-white py-10 px-6 flex justify-between items-center border-t-2 border-primary">
        <span class="text-sm">© {{ currentYear }} DevBiz. All rights reserved.</span>

    </footer>
</template>

<script setup lang="ts">
import { computed } from 'vue'

const currentYear = computed(() => new Date().getFullYear())
</script>