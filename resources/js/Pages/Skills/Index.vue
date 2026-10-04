<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { Head, Link } from '@inertiajs/vue3';
import { computed } from 'vue';

const props = defineProps({
    skills: {
        type: [Array, Object],
        default: () => [],
    },
});

const skillList = computed(() => {
    return Array.isArray(props.skills) ? props.skills : (props.skills?.data || []);
});
</script>

<template>
    <Head title="Skills" />

    <AuthenticatedLayout>
        <template #header>
            <h2 class="text-xl font-semibold leading-tight text-gray-800">
                Skills
            </h2>
        </template>

        <div class="py-12">
            <div class="mx-auto max-w-7xl sm:px-6 lg:px-8">
                <!-- Skills Table / List Card -->
                <div class="overflow-hidden bg-white shadow-sm sm:rounded-lg">
                    <div class="p-6 text-gray-900">
                        <div v-if="skillList.length === 0" class="text-center py-8">
                            <p class="text-gray-500 text-lg">No skills found.</p>
                            <p class="text-gray-400 text-sm mt-1">Get started by creating your first skill.</p>
                            <Link
                                :href="route('skills.create')"
                                class="inline-block mt-4 text-sm font-semibold text-indigo-600 hover:text-indigo-800"
                            >
                                + Add Skill
                            </Link>
                        </div>

                        <div v-else class="relative overflow-x-auto">
                            <div class="flex justify-end mb-4">
                                <Link
                                    :href="route('skills.create')"
                                    class="bg-indigo-500 hover:bg-indigo-700 text-white font-medium py-2 px-4 rounded-md shadow-sm transition text-sm"
                                >
                                    + New Skill
                                </Link>
                            </div>
                            <table class="w-full text-sm text-left text-gray-500">
                                <thead class="text-xs text-gray-700 uppercase bg-gray-50 border-b">
                                    <tr>
                                        <th scope="col" class="px-6 py-3">ID</th>
                                        <th scope="col" class="px-6 py-3">Image</th>
                                        <th scope="col" class="px-6 py-3">Name</th>
                                        <th scope="col" class="px-6 py-3 text-right">Actions</th>
                                    </tr>
                                </thead>
                                <tbody>
                                    <tr
                                        v-for="skill in skillList"
                                        :key="skill.id"
                                        class="bg-white border-b hover:bg-gray-50 transition"
                                    >
                                        <td class="px-6 py-4 font-medium text-gray-900">
                                            {{ skill.id }}
                                        </td>
                                        <td class="px-6 py-4">
                                            <img
                                                v-if="skill.image"
                                                :src="skill.image.startsWith('http') || skill.image.startsWith('/') ? skill.image : '/storage/' + skill.image"
                                                :alt="skill.name"
                                                class="w-12 h-12 rounded object-cover border"
                                            />
                                            <span v-else class="text-gray-400 text-xs italic">No image</span>
                                        </td>
                                        <td class="px-6 py-4 font-medium text-gray-900">
                                            {{ skill.name }}
                                        </td>
                                        <td class="px-6 py-4 text-right space-x-2">
                                            <Link
                                                v-if="route().has('skills.edit')"
                                                :href="route('skills.edit', skill.id)"
                                                class="font-medium text-blue-600 hover:text-blue-900"
                                            >
                                                Edit
                                            </Link>
                                            <Link
                                                v-if="route().has('skills.destroy')"
                                                :href="route('skills.destroy', skill.id)"
                                                method="delete"
                                                as="button"
                                                type="button"
                                                class="font-medium text-red-600 hover:text-red-900"
                                            >
                                                Delete
                                            </Link>
                                        </td>
                                    </tr>
                                </tbody>
                            </table>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </AuthenticatedLayout>
</template>
