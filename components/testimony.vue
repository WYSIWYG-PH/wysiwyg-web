<template>
    <div class="bg-slate-950 py-24 sm:py-32 ">
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

        
            <div class="grid grid-cols-1 gap-8 md:grid-cols-2 lg:grid-cols-3">
                <div v-for="(testimonial, index) in testimonials" :key="testimonial.id"
                    class="relative rounded-2xl bg-gray-800/50 p-6 shadow-lg border border-green-500 transition-all duration-300 hover:shadow-lg hover:shadow-green-500/30"
                    v-motion :initial="{ opacity: 0, scale: 0.9 }" :visible="{
                        opacity: 1,
                        scale: 1,
                        transition: {
                            delay: index * 200,
                            duration: 600,
                            ease: 'easeOut'
                        }
                    }">
                    <!-- Quote icon -->
                    <div class="absolute top-6 right-6 text-green-500/50">
                        <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none"
                            stroke="currentColor" stroke-width="2" class="opacity-60">
                            <path
                                d="M3 21c3 0 7-1 7-8V5c0-1.25-.756-2.017-2-2H4c-1.25 0-2 .75-2 1.972V11c0 1.25.75 2 2 2 1 0 1 0 1 1v1c0 1-1 2-2 2s-1 .008-1 1.031V20c0 1 0 1 1 1z">
                            </path>
                            <path
                                d="M15 21c3 0 7-1 7-8V5c0-1.25-.757-2.017-2-2h-4c-1.25 0-2 .75-2 1.972V11c0 1.25.75 2 2 2h.75c0 2.25.25 4-2.75 4v3c0 1 0 1 1 1z">
                            </path>
                        </svg>
                    </div>

                    <!-- Quote text -->
                    <p class="text-base italic text-gray-300 mb-8">"{{ testimonial.quote }}"</p>

                    <!-- Author info - Horizontal layout -->
                    <div class="flex items-center gap-x-4 mt-6 pt-6 border-t border-green-500/30">
                        <img class="size-12 rounded-full object-cover ring-2 ring-green-500/50" :src="testimonial.image"
                            :alt="testimonial.name">
                        <div>
                            <h3 class="text-base font-semibold tracking-tight text-white">{{ testimonial.name }}</h3>
                            <p class="text-sm font-semibold text-primary">{{ testimonial.company }}</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
import testimonials from '~/data/testimony';
</script>