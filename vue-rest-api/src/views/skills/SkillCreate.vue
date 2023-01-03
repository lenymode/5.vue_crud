<script setup>

    import { reactive } from 'vue';
    import useSkills from '../../composables/skills';

    const { storeSkill, errors} = useSkills();

    const form = reactive ({
        name: "",
        slug: "",
    });
</script>
    

<template>
    <form  class="max-w-md mx-auto p-4 bg-white shadow-md rounded-m" @submit.prevent="storeSkill(form)">
        <div class="space-y-6">
            <div class="mb-6">
                <label for="name" class="block mb-2 text-sm font-medium text-gray-400 dark:text-black">Name</label>
                <input type="text" id="name" v-model="form.name" class="bg-gray-50 border border-gray-300 text-gray-400 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-200 dark:border-gray-300 dark:placeholder-gray-400 dark:text-black dark:focus:ring-blue-500 dark:focus:border-blue-500">
                <div v-if="errors.name">
                    <span class="text-sm text-red-600">{{errors.name[0]}}</span>
                </div>
            </div>
            <div class="mb-6">
                <label for="slug" class="block mb-2 text-sm font-medium text-black-400 dark:text-black">Slug</label>
                <input type="text" id="slug" v-model="form.slug" class="bg-gray-50 border border-gray-300 text-gray-400 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-200 dark:border-gray-300 dark:placeholder-gray-400 dark:text-black dark:focus:ring-blue-500 dark:focus:border-blue-500">
                <div v-if="errors.slug">
                    <span class="text-sm text-red-600">{{errors.slug[0]}}</span>
                </div>
            </div>
        </div>
        <div class="mt-4">
                <button type="submit" class="px-4 py-2 bg-indigo-700 hover:bg-indigo-800 rounded text-white">Save</button>
        </div>

    </form>
</template>