<template>
    <nav
        class="fixed top-4 left-1/2 transform -translate-x-1/2 z-50 w-[90%] max-w-[700px] bg-gray-950/80 backdrop-blur-md shadow-xl rounded-xl px-6 py-3 md:px-12 md:py-4 border border-[#00DC82] hover:shadow-2xl transition-all duration-300 text-white">
        <!-- Desktop Menu -->
        <div class="hidden md:flex justify-center gap-12 items-center">
            <button @click="scrollToSection('services')" class="nav-item flex items-center gap-2">
                <Icon name="ph-wrench" class="size-5 text-[#00DC82]" /> Services
            </button>
            <button @click="scrollToSection('projects')" class="nav-item flex items-center gap-2">
                <Icon name="ph-folder" class="size-5 text-[#00DC82]" /> Projects
            </button>
            <button @click="scrollToSection('testimonials')" class="nav-item flex items-center gap-2">
                <Icon name="ph-quotes" class="size-5 text-[#00DC82]" /> Testimonials
            </button>
            <button @click="scrollToSection('team')" class="nav-item flex items-center gap-2">
                <Icon name="ph-users-three" class="size-5 text-[#00DC82]" /> Our Team
            </button>
        </div>

        <!-- Mobile Menu Button -->
        <div class="flex justify-between items-center md:hidden">
            <span class="font-semibold">Menu</span>
            <button @click="toggleMenu" class="focus:outline-none">
                <Icon name="ph-list" class="size-6 text-white" />
            </button>
        </div>

        <!-- Mobile Dropdown Menu -->
        <div v-if="isOpen" class="mt-4 md:hidden flex flex-col gap-4">
            <button @click="handleMobileClick('services')" class="nav-item flex items-center gap-2">
                <Icon name="ph-wrench" class="size-5 text-[#00DC82]" /> Services
            </button>
            <button @click="handleMobileClick('projects')" class="nav-item flex items-center gap-2">
                <Icon name="ph-folder" class="size-5 text-[#00DC82]" /> Projects
            </button>
            <button @click="handleMobileClick('testimonials')" class="nav-item flex items-center gap-2">
                <Icon name="ph-quotes" class="size-5 text-[#00DC82]" /> Testimonials
            </button>
            <button @click="handleMobileClick('team')" class="nav-item flex items-center gap-2">
                <Icon name="ph-users-three" class="size-5 text-[#00DC82]" /> Our Team
            </button>
        </div>
    </nav>
</template>

<script setup>
import { ref } from 'vue'

const isOpen = ref(false)

const toggleMenu = () => {
    isOpen.value = !isOpen.value
}

const scrollToSection = (id) => {
    const el = document.getElementById(id)
    if (el) {
        el.scrollIntoView({ behavior: 'smooth', block: 'start' })
    }
}

const handleMobileClick = (id) => {
    scrollToSection(id)
    isOpen.value = false
}
</script>

<style scoped>
.nav-item {
    @apply text-sm font-medium hover:text-[#00DC82] transition-colors duration-200;
}
</style>