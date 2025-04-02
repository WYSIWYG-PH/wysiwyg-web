<template>
  <!-- Hero Section -->
  <section class="flex min-h-[500px] bg-gray-900 relative overflow-hidden">
    <div class="w-full flex flex-col md:flex-row items-center h-screen">
      <div class="w-full md:w-1/2 px-6 md:px-8 lg:px-12 xl:px-16 py-12 text-center md:text-left ">
        <h1 class="text-3xl md:text-5xl lg:text-6xl font-extrabold text-white leading-tight mb-6">
          <span v-motion :initial="{ opacity: 0, y: 20 }" :enter="{ opacity: 1, y: 0, transition: { duration: 800 } }">
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
        <p class="text-gray-300 text-lg mb-8 max-w-lg mx-auto md:mx-0" v-motion :initial="{ opacity: 0 }" :enter="{
          opacity: 1,
          transition: {
            delay: 800,
            duration: 800
          }
        }">
          We partner with ambitious businesses to build websites, mobile apps, and software that drive success.
        </p>
        <div class="flex justify-center md:justify-start space-x-4" v-motion :initial="{ opacity: 0, y: 20 }" :enter="{
          opacity: 1,
          y: 0,
          transition: {
            delay: 1200,
            duration: 600
          }
        }">
          <button
            class="bg-primary text-gray-900 px-6 py-3 rounded-md font-medium transition duration-300 hover:bg-primary-400 hover:shadow-[0_0_15px_4px_rgba(0,220,130,0.7)]">
            Discover more
          </button>
        </div>
      </div>
      <div class="w-full md:w-1/2 h-[300px] md:h-auto relative" v-motion :initial="{ opacity: 0, x: 50 }" :enter="{
        opacity: 1,
        x: 0,
        transition: {
          delay: 0,
          duration: 1000
        }
      }">
        <img
          src="https://images.unsplash.com/photo-1614741118887-7a4ee193a5fa?q=80&w=1974&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D"
          alt="Code editor showing development environment" class="w-full h-full object-cover" />
        <div class="absolute inset-0 bg-gradient-to-b md:bg-gradient-to-r from-gray-900 to-transparent"></div>
      </div>
    </div>
  </section>
  <!-- Services Section -->
  <section class="bg-slate-950 py-24 border-y-2 border-primary sm:py-32">
    <div class="mx-auto max-w-7xl px-6 lg:px-8">
      <div class="mx-auto max-w-2xl lg:text-center" v-motion :initial="{ opacity: 0, y: 30 }"
        :visible="{ opacity: 1, y: 0, transition: { duration: 800 } }">
        <p class="mt-2 text-4xl font-semibold tracking-tight text-pretty text-white sm:text-5xl lg:text-balance">
          Our Services</p>
        <p class="mt-6 text-lg/8 text-gray-400">We provide a range of digital solutions to help businesses grow and
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
  </section>
  <!-- Team Section -->
  <section class="bg-gray-900 py-24 sm:py-32">
    <div class="mx-auto grid max-w-7xl gap-20 px-6 lg:px-8 xl:grid-cols-3">
      <div class="max-w-xl" v-motion :initial="{ opacity: 0, y: 30 }"
        :visible="{ opacity: 1, y: 0, transition: { duration: 800 } }">
        <h2 class="text-3xl font-semibold tracking-tight text-pretty text-white sm:text-4xl">Meet our team</h2>
        <p class="mt-6 text-lg/8 text-gray-300">We're a dynamic group of individuals who are passionate about what we
          do and dedicated to delivering the best results for our clients.</p>
      </div>
      <ul role="list" class="grid gap-x-8 gap-y-12 sm:grid-cols-2 sm:gap-y-16 xl:col-span-2">
        <li v-for="(member, index) in teamMembers" :key="index" v-motion :initial="{ opacity: 0, x: 30 }" :visible="{
          opacity: 1,
          x: 0,
          transition: {
            delay: index * 300,
            duration: 800,
            ease: 'easeOut'
          }
        }">
          <div class="flex items-center gap-x-6">
            <img class="size-16 rounded-full" :src="member.image" :alt="member.name">
            <div>
              <h3 class="text-base/7 font-semibold tracking-tight text-white">{{ member.name }}</h3>
              <p class="text-sm/6 font-semibold text-primary">{{ member.position }}</p>
            </div>
          </div>
        </li>
      </ul>
    </div>
  </section>
  <Footer />
</template>

<script setup>
import { ArrowPathIcon, CloudArrowUpIcon, LockClosedIcon } from '@heroicons/vue/20/solid'

const features = [
  {
    name: 'Push to deploy',
    description:
      'Commodo nec sagittis tortor mauris sed. Turpis tortor quis scelerisque diam id accumsan nullam tempus. Pulvinar etiam lacus volutpat eu. Phasellus praesent ligula sit faucibus.',
    href: '#',
    icon: CloudArrowUpIcon,
  },
  {
    name: 'SSL certificates',
    description:
      'Pellentesque enim a commodo malesuada turpis eleifend risus. Facilisis donec placerat sapien consequat tempor fermentum nibh.',
    href: '#',
    icon: LockClosedIcon,
  },
  {
    name: 'Simple queues',
    description:
      'Pellentesque sit elit congue ante nec amet. Dolor aenean curabitur viverra suspendisse iaculis eget. Nec mollis placerat ultricies euismod ut condimentum.',
    href: '#',
    icon: ArrowPathIcon,
  },
]

const services = [
  {
    icon: 'ph-desktop',
    title: 'Web Development',
    description: 'Custom websites built with the latest technologies to ensure performance and scalability.'
  },
  {
    icon: 'ph-android-logo',
    title: 'Mobile App Development',
    description: 'High-quality mobile applications tailored to your business needs.'
  },
  {
    icon: 'ph-code',
    title: 'Software Solutions',
    description: 'Robust and scalable software solutions to enhance business operations.'
  }
];

const teamMembers = [
  {
    name: "Erman Faminiano",
    position: "Full Stack Web/Mobile Developer",
    image: "https://images.unsplash.com/photo-1506794778202-cad84cf45f1d?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80"
  },
  {
    name: "Jonhyl Balsamo",
    position: "Frontend Web/Mobile Developer",
    image: "https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80"
  }
];
</script>
