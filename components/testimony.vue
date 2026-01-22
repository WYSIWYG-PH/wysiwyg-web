<template>
    <div class="bg-slate-950 py-24 sm:py-32 relative">
        <!-- ONE quote icon for whole section -->
        <div class="absolute top-8 right-8 text-green-500/40">
            <svg xmlns="http://www.w3.org/2000/svg" width="54" height="54" viewBox="0 0 24 24" fill="none"
                stroke="currentColor" stroke-width="1.5" class="opacity-80">
                <path
                    d="M3 21c3 0 7-1 7-8V5c0-1.25-.756-2.017-2-2H4c-1.25 0-2 .75-2 1.972V11c1.25 0 2 .75 2 2 1 0 1 0 1 1v1c0 1-1 2-2 2s-1 .008-1 1.031V20c0 1 0 1 1 1z">
                </path>
                <path
                    d="M15 21c3 0 7-1 7-8V5c0-1.25-.757-2.017-2-2h-4c-1.25 0-2 .75-2 1.972V11c1.25 0 .75 2 2 2h.75c0 2.25.25 4-2.75 4v3c0 1 0 1 1 1z">
                </path>
            </svg>
        </div>
        <div class="mx-auto max-w-7xl px-6 lg:px-8">
            <!-- Header Section - Centered -->
            <div class="mx-auto max-w-2xl text-center mb-16" v-motion :initial="{ opacity: 0, y: 30 }"
                :visible="{ opacity: 1, y: 0, transition: { duration: 800 } }">
                <h2 class="text-3xl font-semibold tracking-tight text-white sm:text-4xl">What our clients say</h2>
                <p class="mt-6 text-lg/8 text-gray-300">
                    Don't just take our word for it. Hear from some of our amazing clients about their experiences
                    working with our team.
                </p>
            </div>

            <!-- Carousel Container -->
            <div class="relative">
                <!-- Navigation Arrows (only show if more than 3 testimonials) -->
                <button v-if="testimonials.length > 3" @click="previousSlide"
                    class="absolute left-0 top-1/2 -translate-y-1/2 -translate-x-4 z-10 bg-gray-800/80 hover:bg-gray-700 text-green-500 rounded-full p-3 shadow-lg border border-green-500/50 transition-all duration-300 hover:scale-110 disabled:opacity-50 disabled:cursor-not-allowed"
                    :disabled="currentSlide === 0">
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24"
                        stroke="currentColor" stroke-width="2">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M15 19l-7-7 7-7" />
                    </svg>
                </button>

                <button v-if="testimonials.length > 3" @click="nextSlide"
                    class="absolute right-0 top-1/2 -translate-y-1/2 translate-x-4 z-10 bg-gray-800/80 hover:bg-gray-700 text-green-500 rounded-full p-3 shadow-lg border border-green-500/50 transition-all duration-300 hover:scale-110 disabled:opacity-50 disabled:cursor-not-allowed"
                    :disabled="currentSlide >= totalSlides - 1">
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24"
                        stroke="currentColor" stroke-width="2">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M9 5l7 7-7 7" />
                    </svg>
                </button>

                <!-- Testimonials Grid/Carousel -->
                <div class="overflow-hidden">
                    <div class="flex transition-transform duration-500 ease-in-out"
                        :style="{ transform: `translateX(-${currentSlide * 100}%)` }">
                        <div v-for="(group, groupIndex) in testimonialGroups" :key="groupIndex"
                            class="w-full flex-shrink-0 grid grid-cols-1 gap-8 md:grid-cols-2 lg:grid-cols-2">
                            <div v-for="testimonial in group" :key="testimonial.id"
                                class="relative rounded-2xl bg-gray-800/50 p-6 shadow-lg border border-green-500 transition-all duration-300 hover:shadow-lg hover:shadow-green-500/30 flex flex-col h-full"
                                v-motion :initial="{ opacity: 0, scale: 0.9 }"
                                :visible="{ opacity: 1, scale: 1, transition: { duration: 600, ease: 'easeOut' } }">

                                <!-- Quote text - flex-grow to fill space -->
                                <p class="text-base italic text-gray-300 mb-6 flex-grow">"{{ testimonial.quote }}"</p>

                                <!-- Fixed Author info -->
                                <div class="flex items-center gap-x-4 mt-auto pt-4 border-t border-green-500/30">
                                    <img class="w-12 h-12 rounded-full object-cover ring-2 ring-green-500/50"
                                        :src="testimonial.image" :alt="testimonial.name">
                                    <div>
                                        <h3 class="text-base font-semibold tracking-tight text-white">{{
                                            testimonial.name }}</h3>
                                        <p class="text-sm font-semibold text-green-400">{{ testimonial.company }}</p>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Carousel Indicators (only show if more than 3 testimonials) -->
                <div v-if="testimonials.length > 3" class="flex justify-center gap-2 mt-8">
                    <button v-for="(slide, index) in totalSlides" :key="index" @click="goToSlide(index)"
                        class="h-2 rounded-full transition-all duration-300"
                        :class="currentSlide === index ? 'w-8 bg-green-500' : 'w-2 bg-gray-600 hover:bg-gray-500'">
                    </button>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
import { ref, computed } from 'vue';
import testimonials from '~/data/testimony';

const currentSlide = ref(0);
const cardsPerView = 4;

// Calculate total number of slides
const totalSlides = computed(() => {
    if (testimonials.length <= cardsPerView) return 1;
    return Math.ceil(testimonials.length / cardsPerView);
});

// Group testimonials into sets of 3
const testimonialGroups = computed(() => {
    const groups = [];
    for (let i = 0; i < testimonials.length; i += cardsPerView) {
        groups.push(testimonials.slice(i, i + cardsPerView));
    }
    return groups;
});

const nextSlide = () => {
    if (currentSlide.value < totalSlides.value - 1) {
        currentSlide.value++;
    }
};

const previousSlide = () => {
    if (currentSlide.value > 0) {
        currentSlide.value--;
    }
};

const goToSlide = (index) => {
    currentSlide.value = index;
};
</script>