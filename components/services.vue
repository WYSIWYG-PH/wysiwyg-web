<template>
    <div class="bg-slate-900 py-24 sm:py-32">
        <div class="mx-auto max-w-7xl px-6 lg:px-8">
            <div class="mx-auto max-w-2xl lg:text-center" v-motion :initial="{ opacity: 0, y: 30 }"
                :visible="{ opacity: 1, y: 0, transition: { duration: 800 } }">
                <p
                    class="mt-2 text-4xl font-semibold tracking-tight text-pretty text-white sm:text-5xl lg:text-balance">
                    Our Services</p>
                <p class="mt-6 text-lg/8 text-gray-400">We provide a range of digital solutions to help businesses grow
                    and
                    succeed.</p>
            </div>
            <div class="mx-auto mt-16 max-w-2xl sm:mt-20 lg:mt-24 lg:max-w-none">
                <dl class="grid max-w-xl grid-cols-1 gap-x-8 gap-y-16 lg:max-w-none lg:grid-cols-3">
                    <div v-for="(service, index) in services" :key="index" class="flex flex-col" v-motion
                        :initial="{ opacity: 0, y: 50 }" :visible="{
                            opacity: 1,
                            y: 0,
                            transition: {
                                delay: index * 200,
                                duration: 800
                            }
                        }">
                        <dt class="flex items-center gap-x-3 text-base/7 font-semibold text-white">
                            <Icon :name="service.icon" class="size-5 flex-none text-primary" aria-hidden="true" />
                            {{ service.title }}
                        </dt>
                        <dd class="mt-4 flex flex-auto flex-col text-base/7 text-gray-400">
                            <p class="flex-auto">
                                {{ service.description }}
                            </p>
                        </dd>
                    </div>
                </dl>
            </div>
        </div>
    </div>
</template>

<script setup>
import services from '~/data/services';
</script>