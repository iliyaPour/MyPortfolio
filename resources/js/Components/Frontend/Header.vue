<script setup>
import { ref } from 'vue';

const showMobileMenu = ref(false);
</script>

<template>
    <nav class="bg-light-primary dark:bg-dark-primary fixed w-full z-20 top-0 start-0 border-b border-gray-200 dark:border-gray-800">
        <div class="max-w-screen-xl flex flex-wrap items-center justify-between mx-auto p-4">
            <a href="https://flowbite.com/" class="flex items-center space-x-3 rtl:space-x-reverse">
                <img src="https://flowbite.com/docs/images/logo.svg" class="h-7" alt="Flowbite Logo" />
                <span class="self-center text-xl text-gray-900 dark:text-white font-semibold whitespace-nowrap">Flowbite</span>
            </a>
            <button
                @click="showMobileMenu = !showMobileMenu"
                type="button"
                class="inline-flex items-center p-2 w-10 h-10 justify-center text-sm text-gray-500 rounded-lg md:hidden hover:bg-gray-100 focus:outline-none focus:ring-2 focus:ring-gray-200 dark:text-gray-400 dark:hover:bg-gray-700 dark:focus:ring-gray-600"
                aria-controls="navbar-default"
                :aria-expanded="showMobileMenu"
            >
                <span class="sr-only">Open main menu</span>
                <svg class="w-6 h-6" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="none" viewBox="0 0 24 24">
                    <path stroke="currentColor" stroke-linecap="round" stroke-width="2" d="M5 7h14M5 12h14M5 17h14"/>
                </svg>
            </button>
            <div class="w-full md:block md:w-auto" :class="{ hidden: !showMobileMenu }" id="navbar-default">
                <ul class="font-medium flex flex-col p-4 md:p-0 mt-4 border border-gray-200 dark:border-gray-700 rounded-lg bg-light-secondary dark:bg-dark-secondary md:flex-row md:space-x-8 rtl:space-x-reverse md:mt-0 md:border-0 md:bg-transparent md:dark:bg-transparent">
                    <li>
                        <a href="#" class="block py-2 px-3 text-white bg-light-tail-500 dark:bg-dark-navy-100 rounded md:bg-transparent md:text-accent md:p-0" aria-current="page">Home</a>
                    </li>
                    <li>
                        <a href="#about" class="block py-2 px-3 text-gray-900 dark:text-white rounded hover:bg-gray-100 dark:hover:bg-gray-700 md:hover:bg-transparent md:border-0 md:hover:text-accent md:p-0 md:dark:hover:bg-transparent md:dark:hover:text-accent">About</a>
                    </li>
                    <li>
                        <a href="#services" class="block py-2 px-3 text-gray-900 dark:text-white rounded hover:bg-gray-100 dark:hover:bg-gray-700 md:hover:bg-transparent md:border-0 md:hover:text-accent md:p-0 md:dark:hover:bg-transparent md:dark:hover:text-accent">Services</a>
                    </li>
                    <li>
                        <a href="#pricing" class="block py-2 px-3 text-gray-900 dark:text-white rounded hover:bg-gray-100 dark:hover:bg-gray-700 md:hover:bg-transparent md:border-0 md:hover:text-accent md:p-0 md:dark:hover:bg-transparent md:dark:hover:text-accent">Pricing</a>
                    </li>
                    <li>
                        <a href="#contact" class="block py-2 px-3 text-gray-900 dark:text-white rounded hover:bg-gray-100 dark:hover:bg-gray-700 md:hover:bg-transparent md:border-0 md:hover:text-accent md:p-0 md:dark:hover:bg-transparent md:dark:hover:text-accent">Contact</a>
                    </li>
                </ul>
            </div>
        </div>
    </nav>
</template>
