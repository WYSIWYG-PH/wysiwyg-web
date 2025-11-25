<template>
    <div class="bg-gray-900 py-24 sm:py-32">
        <div class="mx-auto grid max-w-7xl gap-20 px-6 lg:px-8 xl:grid-cols-3">
            <div class="max-w-xl" v-motion :initial="{ opacity: 0, y: 30 }"
                :visible="{ opacity: 1, y: 0, transition: { duration: 800 } }">
                <h2 class="text-3xl font-semibold tracking-tight text-pretty text-white sm:text-4xl">Meet our team</h2>
                <p class="mt-6 text-lg/8 text-gray-300">We're a dynamic group of individuals who are passionate about
                    what
                    we
                    do and dedicated to delivering the best results for our clients.</p>
            </div>
            <ul role="list" class="grid gap-8 sm:grid-cols-2 xl:col-span-2">
                <li v-for="(member, index) in teamMembers" :key="index" v-motion :initial="{ opacity: 0, y: 30 }"
                    :visible="{
                        opacity: 1,
                        y: 0,
                        transition: {
                            delay: index * 300,
                            duration: 800
                        }
                    }" class="bg-gray-800 p-6 rounded-2xl border border-gray-700 hover:border-primary transition">

                    <div class="flex items-center gap-4">
                        <img class="w-20 h-20 rounded-lg object-cover" :src="member.image" :alt="member.name">
                        <div>
                            <h3 class="text-xl font-semibold text-white">{{ member.name }}</h3>
                            <p class="text-sm font-medium text-primary">{{ member.position }}</p>
                        </div>
                    </div>

                    <p class="mt-4 text-gray-300 text-sm leading-relaxed">
                        {{ member.description }}
                    </p>
                </li>
            </ul>

        </div>
    </div>
</template>


<script setup>
import teamMembers from '~/data/team';
</script>