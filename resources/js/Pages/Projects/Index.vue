<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { Head, Link } from '@inertiajs/vue3';
import { computed } from 'vue';

const props = defineProps({
    projects: {
        type: [Array, Object],
        default: () => [],
    },
});

const projectList = computed(() => {
    return Array.isArray(props.projects) ? props.projects : (props.projects?.data || []);
});
</script>

<template>
    <Head title="Projects" />

    <AuthenticatedLayout>
        <template #header>
            <h2 class="text-xl font-semibold leading-tight text-gray-800">
                Projects
            </h2>
        </template>

        <div class="py-12">
            <div class="mx-auto max-w-7xl sm:px-6 lg:px-8">
                <!-- Projects Table / List -->
                <div class="overflow-hidden bg-white shadow-sm sm:rounded-lg">
                    <div class="p-6 text-gray-900">
                        <div v-if="projectList.length === 0" class="text-center py-8">
                            <p class="text-gray-500 text-lg">No projects found.</p>
                            <p class="text-gray-400 text-sm mt-1">Get started by creating your first project.</p>
                            <Link
                                :href="route('projects.create')"
                                class="inline-block mt-4 text-sm font-semibold text-indigo-600 hover:text-indigo-800"
                            >
                                + Add Project
                            </Link>
                        </div>

                        <div v-else class="relative overflow-x-auto">
                            <table class="w-full text-sm text-left text-gray-500">
                                <thead class="text-xs text-gray-700 uppercase bg-gray-50 border-b">
                                    <tr>
                                        <th scope="col" class="px-6 py-3">ID</th>
                                        <th scope="col" class="px-6 py-3">Image</th>
                                        <th scope="col" class="px-6 py-3">Name</th>
                                        <th scope="col" class="px-6 py-3">Skill</th>
                                        <th scope="col" class="px-6 py-3">URL</th>
                                        <th scope="col" class="px-6 py-3 text-right">Actions</th>
                                    </tr>
                                </thead>
                                <tbody>
                                    <tr
                                        v-for="project in projectList"
                                        :key="project.id"
                                        class="bg-white border-b hover:bg-gray-50 transition"
                                    >
                                        <td class="px-6 py-4 font-medium text-gray-900">
                                            {{ project.id }}
                                        </td>
                                        <td class="px-6 py-4">
                                            <img
                                                v-if="project.image"
                                                :src="project.image.startsWith('http') || project.image.startsWith('/') ? project.image : '/storage/' + project.image"
                                                :alt="project.name"
                                                class="w-12 h-12 rounded object-cover border"
                                            />
                                            <span v-else class="text-gray-400 text-xs italic">No image</span>
                                        </td>
                                        <td class="px-6 py-4 font-medium text-gray-900">
                                            {{ project.name }}
                                        </td>
                                        <td class="px-6 py-4">
                                            <span
                                                v-if="project.skill"
                                                class="inline-flex items-center px-2.5 py-0.5 rounded-full text-xs font-medium bg-indigo-100 text-indigo-800"
                                            >
                                                {{ project.skill.name }}
                                            </span>
                                            <span v-else class="text-gray-400 text-xs italic">N/A</span>
                                        </td>
                                        <td class="px-6 py-4">
                                            <a
                                                v-if="project.project_url"
                                                :href="project.project_url"
                                                target="_blank"
                                                rel="noopener noreferrer"
                                                class="text-indigo-600 hover:text-indigo-900 underline truncate max-w-xs block"
                                            >
                                                {{ project.project_url }}
                                            </a>
                                            <span v-else class="text-gray-400 text-xs italic">None</span>
                                        </td>
                                        <td class="px-6 py-4 text-right space-x-2">
                                            <Link
                                                v-if="route().has('projects.edit')"
                                                :href="route('projects.edit', project.id)"
                                   d             class="font-medium text-blue-600 hover:text-blue-900"
                                            >
                                                Edit
                                            </Link>
                                            <Link
                                                v-if="route().has('projects.destroy')"
                                                :href="route('projects.destroy', project.id)"
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
