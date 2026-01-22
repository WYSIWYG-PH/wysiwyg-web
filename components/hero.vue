<template>
    <!-- Mobile view: Absolute positioning with centered text -->
    <div class="flex min-h-[500px] h-screen bg-gray-900 relative overflow-hidden">

        <div class="absolute inset-0 md:hidden w-full h-full">
            <img src="https://images.unsplash.com/photo-1614741118887-7a4ee193a5fa?q=80&w=1974&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D"
                alt="Code editor showing development environment" class="w-full h-full object-cover" />
            <div class="absolute inset-0 bg-gray-900 bg-opacity-70"></div>
        </div>


        <div class="absolute inset-0 flex items-center justify-center md:hidden">
            <div class="w-full px-6 py-12 text-center flex flex-col items-center">
                <h1 class="text-4xl font-extrabold text-white leading-tight mb-6">
                    <span v-motion :initial="{ opacity: 0, y: 20 }"
                        :enter="{ opacity: 1, y: 0, transition: { duration: 800 } }">
                        Driving business success with
                    </span>
                    <span class="text-primary" v-motion :initial="{ opacity: 0, scale: 0.9 }" :enter="{
                        opacity: 1,
                        scale: 1,
                        transition: {
                            delay: 400,
                            duration: 800,
                            ease: 'easeOut'
                        }
                    }">
                        innovative solutions.
                    </span>
                </h1>
                <p class="text-gray-300 text-lg mb-8 max-w-lg mx-auto" v-motion :initial="{ opacity: 0 }" :enter="{
                    opacity: 1,
                    transition: {
                        delay: 800,
                        duration: 800
                    }
                }">
                    We partner with ambitious businesses to build websites, mobile apps, and software that drive
                    success.
                </p>
                <div class="flex justify-center space-x-4" v-motion :initial="{ opacity: 0, y: 20 }" :enter="{
                    opacity: 1,
                    y: 0,
                    transition: {
                        delay: 1200,
                        duration: 600
                    }
                }">
                    <button
                        class="bg-primary text-gray-800 px-6 py-3 rounded-md font-medium transition duration-300 hover:bg-primary-400 hover:shadow-[0_0_15px_4px_rgba(0,220,130,0.7)]"
                        onclick="window.location.href='https://www.facebook.com/profile.php?id=61586726650291'">
                        Visit Us
                    </button>
                </div>
            </div>
        </div>

        <!-- Desktop view: Exactly as in the original -->
        <div class="hidden md:flex w-full flex-row items-center h-screen">
            <div class="w-2/3 px-8 lg:px-12 xl:px-16 py-12 text-left">
                <h1 class="text-5xl lg:text-6xl font-extrabold text-white leading-tight mb-6">
                    <span v-motion :initial="{ opacity: 0, y: 20 }"
                        :enter="{ opacity: 1, y: 0, transition: { duration: 800 } }">
                        Driving business success with
                    </span>
                    <span class="text-primary" v-motion :initial="{ opacity: 0, scale: 0.9 }" :enter="{
                        opacity: 1,
                        scale: 1,
                        transition: {
                            delay: 400,
                            duration: 800,
                            ease: 'easeOut'
                        }
                    }">
                        innovative solutions.
                    </span>
                </h1>
                <p class="text-gray-300 text-lg mb-8 max-w-lg" v-motion :initial="{ opacity: 0 }" :enter="{
                    opacity: 1,
                    transition: {
                        delay: 800,
                        duration: 800
                    }
                }">
                    We partner with ambitious businesses to build websites, mobile apps, and software that drive
                    success.
                </p>
                <div class="flex justify-start space-x-4" v-motion :initial="{ opacity: 0, y: 20 }" :enter="{
                    opacity: 1,
                    y: 0,
                    transition: {
                        delay: 1200,
                        duration: 600
                    }
                }">
                    <button
                        class="bg-primary text-gray-800 px-6 py-3 rounded-md font-medium transition duration-300 hover:bg-primary-400 hover:shadow-[0_0_15px_4px_rgba(0,220,130,0.7)]"
                        onclick="window.location.href='https://www.facebook.com/profile.php?id=61586726650291'">
                        Visit Us
                    </button>
                </div>
            </div>
            <div class="w-1/2 h-auto relative" v-motion :initial="{ opacity: 0, x: 50 }" :enter="{
                opacity: 1,
                x: 0,
                transition: {
                    delay: 0,
                    duration: 1000
                }
            }">
                <img src="https://images.unsplash.com/photo-1614741118887-7a4ee193a5fa?q=80&w=1974&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D"
                    alt="Code editor showing development environment" class="w-full h-full object-cover" />
                <div class="absolute inset-0 bg-gradient-to-r from-gray-900 to-transparent"></div>
            </div>
        </div>
    </div>
</template>