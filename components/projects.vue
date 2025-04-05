<template>
    <section class="bg-slate-950 py-16 border-t border-b border-primary">
        <div class="container mx-auto px-4">
            <!-- Section Header -->
            <div class="mb-12 text-center">
                <h2 class="text-3xl font-bold text-white mb-4">Our Projects</h2>
                <p class="text-gray-400 max-w-2xl mx-auto">Explore our portfolio of successful projects that showcase
                    our expertise and commitment to excellence.</p>
            </div>

            <!-- Projects Grid -->
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
                <div v-for="(project, index) in projects" :key="index" class="bg-slate-900 rounded-lg overflow-hidden">
                    <div class="h-48 overflow-hidden">
                        <img :src="project.image" :alt="project.title" class="w-full h-full object-cover">
                    </div>
                    <div class="p-6">
                        <span
                            class="inline-block px-3 py-1 text-xs font-medium bg-primary bg-opacity-20 text-primary rounded-full mb-4">{{
                            project.category }}</span>
                        <h3 class="text-xl font-semibold text-white mb-3">{{ project.title }}</h3>
                        <p class="text-gray-400 mb-4">{{ project.description }}</p>
                        <div class="flex justify-between items-center">
                            <span class="text-sm text-gray-500">{{ project.date }}</span>
                            <button
                                class="text-primary hover:text-white transition duration-200 flex items-center gap-1">
                                View Details
                                <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4" fill="none" viewBox="0 0 24 24"
                                    stroke="currentColor">
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                        d="M9 5l7 7-7 7" />
                                </svg>
                            </button>
                        </div>
                    </div>
                </div>
            </div>

            <!-- View All Projects Button -->
            <div class="mt-12 text-center">
                <button
                    class="px-6 py-3 bg-primary text-white font-medium rounded-lg hover:bg-opacity-90 transition duration-200">
                    View All Projects
                </button>
            </div>
        </div>
    </section>
</template>

<script setup>
// Sample project data - you can replace this with your actual data source
const projects = [
    {
        title: "E-commerce Platform Redesign",
        description: "Complete overhaul of an online store with improved UX/UI and payment processing integration.",
        image: "/images/projects/ecommerce.jpg",
        category: "Web Development",
        date: "January 2025"
    },
    {
        title: "Real Estate Mobile App",
        description: "iOS and Android application for property listings with virtual tours and mortgage calculator.",
        image: "/images/projects/mobile-app.jpg",
        category: "Mobile Development",
        date: "December 2024"
    },
    {
        title: "Data Analytics Dashboard",
        description: "Interactive dashboard for visualizing business metrics and generating AI-powered insights.",
        image: "/images/projects/dashboard.jpg",
        category: "Data Analytics",
        date: "October 2024"
    },
    {
        title: "Brand Identity Redesign",
        description: "Complete brand refresh including logo design, color palette, and marketing materials.",
        image: "/images/projects/branding.jpg",
        category: "Branding",
        date: "September 2024"
    },
    {
        title: "Enterprise CRM System",
        description: "Custom CRM solution for managing customer relationships, sales, and marketing campaigns.",
        image: "/images/projects/crm.jpg",
        category: "Enterprise Software",
        date: "August 2024"
    },
    {
        title: "AI-Powered Chatbot",
        description: "Intelligent customer service solution with natural language processing capabilities.",
        image: "/images/projects/chatbot.jpg",
        category: "AI & Machine Learning",
        date: "July 2024"
    }
];
</script>