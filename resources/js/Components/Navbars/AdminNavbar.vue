<template>
    <!-- Navbar -->
    <nav
        class="absolute top-0 left-0 z-10 flex items-center w-full p-4 bg-transparent md:flex-row md:flex-nowrap md:justify-start">
        <div class="flex flex-wrap items-center justify-between w-full px-4 mx-autp md:flex-nowrap md:px-10">
            <!-- Brand -->
            <p class="hidden text-sm font-semibold text-white uppercase lg:inline-block">
                <slot name="breadcrumb"/>
            </p>

            <!-- Form -->
            <form
                @submit.prevent="searchProduct"
                class="flex-row flex-wrap items-center hidden mr-3 md:flex lg:ml-auto"
            >
                <div class="relative flex flex-wrap items-stretch w-full">
                    <span
                        class="absolute z-10 items-center justify-center w-8 h-full py-3 pl-3 text-base font-normal leading-snug text-center bg-transparent rounded text-blueGray-300"
                    >
                        <i class="fas fa-search"></i>
                    </span>
                    <input
                        type="text"
                        placeholder="Search product..."
                        v-model="form.keyword"
                        class="relative w-full px-3 py-3 pl-10 text-sm bg-white border-0 rounded shadow outline-none placeholder-blueGray-300 text-blueGray-600 focus:outline-none focus:ring"
                    />
                </div>
            </form>
            <!-- User -->
            <ul class="flex-col items-center hidden list-none md:flex-row md:flex">
                <UserDropdown/>
            </ul>
        </div>
    </nav>
    <!-- End Navbar -->
</template>

<script setup>
import UserDropdown from "@/Components/Dropdowns/UserDropdown.vue";
import {useForm} from "@inertiajs/vue3";
import {showToast} from "@/Utils/Helper.js";

const form = useForm({
    keyword: null,
});

const searchProduct = () => {
    form.get(route('carts.index'), {
        preserveScroll: true,
    });
};
</script>
