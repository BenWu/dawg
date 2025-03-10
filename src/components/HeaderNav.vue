<script setup lang="ts">
import DarkmodeToggle from '@/components/DarkmodeToggle.vue'

import { onMounted } from 'vue'

import { initFlowbite } from 'flowbite'
// Flowbite is used by the 
onMounted(() => {
    initFlowbite();
})
</script>
<template>
    <nav class="bg-gray-900 fixed w-full z-20 top-0 start-0 border-b border-gray-600">
        <div class="max-w-screen-xl flex flex-wrap items-center justify-between mx-auto p-4">
            <RouterLink id="home-link" to="/" class="flex items-center space-x-3 rtl:space-x-reverse">
                <img src="@/assets/dawg.svg" class="h-12" alt="Data Access Workgroups Logo">
                <span class="self-center text-2xl font-semibold text-white">Data Access <span
                        class="text-transparent bg-clip-text bg-gradient-to-r from-blue-500 to-orange-400">Workgroups</span></span>
            </RouterLink>
            <button data-collapse-toggle="navbar-dropdown" type="button"
                class="inline-flex items-center p-2 w-10 h-10 justify-center text-sm text-gray-500 rounded-lg md:hidden hover:bg-gray-100 focus:outline-none focus:ring-2 focus:ring-gray-200 dark:text-gray-400 dark:hover:bg-gray-700 dark:focus:ring-gray-600"
                aria-controls="navbar-dropdown" aria-expanded="false">
                <span class="sr-only">Open main menu</span>
                <svg class="w-5 h-5" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none"
                    viewBox="0 0 17 14">
                    <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                        d="M1 1h15M1 7h15M1 13h15" />
                </svg>
            </button>
            <div class="w-full md:block md:w-auto" id="navbar-dropdown">
                <ul
                    class="flex flex-col font-medium p-4 md:p-0 mt-4 border rounded-lg md:space-x-8 rtl:space-x-reverse md:flex-row md:mt-0 md:border-0 bg-gray-800 md:bg-gray-900 border-gray-700">
                    <li>
                        <RouterLink
                            class="block py-2 px-3 text-white rounded md:p-0 md:text-blue-500 bg-blue-600 md:bg-transparent"
                            to="/">Home</RouterLink>
                    </li>
                    <li>
                        <a href="https://github.com/mozilla/dawg/blob/main/FAQ.md"
                            class="block py-2 px-3 rounded md:border-0 md:p-0 text-white md:hover:text-blue-500 hover:bg-gray-700 hover:text-white md:hover:bg-transparent">Guide</a>
                    </li>

                    <li>
                        <button id="dropdownNavbarLink" data-dropdown-toggle="dropdownNavbar"
                            class="flex items-center justify-between w-full py-2 px-3 rounded md:border-0 md:p-0 md:w-auto text-white md:hover:text-blue-500 dark:focus:text-white border-gray-700 hover:bg-gray-700 md:hover:bg-transparent">
                            Documentation
                            <svg class="w-2.5 h-2.5 ms-2.5" aria-hidden="true" xmlns="http://www.w3.org/2000/svg"
                                fill="none" viewBox="0 0 10 6">
                                <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round"
                                    stroke-width="2" d="m1 1 4 4 4-4" />
                            </svg></button>
                        <!-- Dropdown menu -->
                        <div id="dropdownNavbar"
                            class="z-10 hidden font-normal divide-y rounded-lg shadow w-44 bg-gray-700 divide-gray-600">
                            <ul class="py-2 text-sm text-gray-400" aria-labelledby="dropdownLargeButton">
                                <li>
                                    <a href="https://mozilla-hub.atlassian.net/wiki/spaces/SRE/pages/27924789/Data+Access+Workgroups"
                                        class="block px-4 py-2 hover:bg-gray-600 hover:text-white">Data Access
                                        Workgroups</a>
                                </li>
                                <li>
                                    <a href="https://mozilla-hub.atlassian.net/wiki/spaces/SRE/pages/27919274/Using+workgroups"
                                        class="block px-4 py-2 hover:bg-gray-600 hover:text-white">GCPv2 Workgroups</a>
                                </li>
                                <li>
                                    <a href="https://wiki.mozilla.org/Security/Data_Classification"
                                        class="block px-4 py-2 hover:bg-gray-600 hover:text-white">Data Classification
                                        at Mozilla</a>
                                </li>
                                <li>
                                    <a href="https://wiki.mozilla.org/Data_Collection#Data_Collection_Categories"
                                        class="block px-4 py-2 hover:bg-gray-600 hover:text-white">Data Collection at
                                        Mozilla</a>
                                </li>
                            </ul>
                        </div>
                    </li>
                    <li>
                        <a href="https://groups.google.com/my-groups"
                            class="block py-2 px-3 rounded md:border-0 md:p-0 text-white md:hover:text-blue-500 hover:bg-gray-700 hover:text-white md:hover:bg-transparent">Google
                            Groups</a>
                    </li>
                    <li>
                        <DarkmodeToggle />
                    </li>
                </ul>
            </div>
        </div>
    </nav>
</template>

<style scoped>
nav {
    --mobile-toggle-width: 40px;
}

#home-link {
    width: calc(100% - var(--mobile-toggle-width))
}

button {
    width: var(--mobile-toggle-width);
}

/* Override some behaviors for the mobile view so we don't have menu-in-menu */
@media (max-width: 639px) {
    #dropdownNavbarLink {
        cursor: default;
    }

    #dropdownNavbar {
        display: inline-block;
        position: relative !important;
        transform: none !important;
        width: 100% !important;
        background-color: transparent;
    }
}


@media (min-width: 640px) {

    #home-link,
    button {
        width: auto;

    }

    #navbar-dropdown ul {
        display: flex;
        align-items: center;
    }

    #dropdownNavbar ul {
        display: inline-block;
    }

    li {
        display: inline-block;
        height: auto
    }
}
</style>
