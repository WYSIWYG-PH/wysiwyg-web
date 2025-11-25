<template>
    <section class="bg-slate-950 py-16 border-t border-b border-primary">
        <div class="container mx-auto px-4">
            <div class="mb-12 text-center">
                <h2 class="text-3xl font-bold text-white mb-4">Our Projects</h2>
                <p class="text-gray-400 max-w-2xl mx-auto">Explore our portfolio of successful projects that showcase
                    our expertise and commitment to excellence.</p>
            </div>

            <div class="relative">
                <!-- Carousel Container -->
                <div class="overflow-hidden">
                    <div class="flex transition-transform duration-500 ease-out"
                        :style="{ transform: `translateX(-${currentIndex * 100}%)` }" @mouseenter="pauseAutoSlide"
                        @mouseleave="resumeAutoSlide">
                        <div v-for="(project, index) in projects" :key="index" class="w-full flex-shrink-0 px-2">
                            <div class="bg-slate-900 rounded-lg overflow-hidden max-w-2xl mx-auto">
                                <div class="h-64 overflow-hidden">
                                    <img :src="project.image" :alt="project.title" class="w-full h-full object-cover">
                                </div>
                                <div class="p-6">
                                    <span
                                        class="inline-block px-3 py-1 text-xs font-medium bg-primary bg-opacity-20 text-primary rounded-full mb-4">
                                        {{ project.category }}
                                    </span>
                                    <h3 class="text-xl font-semibold text-white mb-3">
                                        {{ project.title }}
                                    </h3>
                                    <p class="text-gray-400 mb-4">
                                        {{ project.description }}
                                    </p>
                                    <div v-if="project.link">
                                        <a :href="project.link" target="_blank"
                                            class="inline-block mt-2 px-4 py-2 bg-primary text-white rounded-md hover:bg-opacity-90 transition">
                                            Visit Website
                                        </a>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Dots + Arrows Centered Under Carousel -->
                <div class="flex items-center justify-center gap-4 mt-8">

                    <!-- Left Arrow -->
                    <button @click="prevSlide"
                        class="bg-slate-800 hover:bg-slate-700 text-white w-10 h-10 rounded-full transition shadow-lg flex items-center justify-center mr-5">
                        <Icon name="ph:caret-left" class="size-5 text-primary" />
                    </button>

                    <!-- Dots -->
                    <div class="flex gap-2">
                        <button v-for="(project, index) in projects" :key="index" @click="goToSlide(index)"
                            class="h-2 rounded-full transition-all"
                            :class="currentIndex === index ? 'bg-primary w-8' : 'bg-slate-600 w-2 hover:bg-slate-500'"></button>
                    </div>

                    <!-- Right Arrow -->
                    <button @click="nextSlide"
                        class="bg-slate-800 hover:bg-slate-700 text-white w-10 h-10 rounded-full transition shadow-lg flex items-center justify-center ml-5">
                        <Icon name="ph:caret-right" class="size-5 text-primary" />
                    </button>

                </div>
            </div>
        </div>
    </section>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue';
import projects from '~/data/projects';

const currentIndex = ref(0);
let autoSlideInterval = null;

const nextSlide = () => {
    currentIndex.value = (currentIndex.value + 1) % projects.length;
};

const prevSlide = () => {
    currentIndex.value = (currentIndex.value - 1 + projects.length) % projects.length;
};

const goToSlide = (index) => {
    currentIndex.value = index;
};

const startAutoSlide = () => {
    autoSlideInterval = setInterval(() => {
        nextSlide();
    }, 5000); // Auto-slide every 5 seconds
};

const stopAutoSlide = () => {
    if (autoSlideInterval) {
        clearInterval(autoSlideInterval);
        autoSlideInterval = null;
    }
};

const pauseAutoSlide = () => {
    stopAutoSlide();
};

const resumeAutoSlide = () => {
    startAutoSlide();
};

onMounted(() => {
    startAutoSlide();
});

onUnmounted(() => {
    stopAutoSlide();
});
</script>