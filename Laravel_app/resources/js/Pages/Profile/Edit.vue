<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import DeleteUserForm from './Partials/DeleteUserForm.vue';
import UpdatePasswordForm from './Partials/UpdatePasswordForm.vue';
import UpdateProfileInformationForm from './Partials/UpdateProfileInformationForm.vue';
import { Head } from '@inertiajs/vue3';

defineProps({
    mustVerifyEmail: {
        type: Boolean,
    },
    status: {
        type: String,
    },
});
</script>

<template>
    <Head title="Profile" />

    <AuthenticatedLayout>
        <!-- Overlay con fondo oscuro -->
        <div class="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50 p-4">
            <!-- Modal Container -->
            <div class="bg-white dark:bg-gray-800 rounded-lg shadow-2xl max-w-4xl w-full max-h-[90vh] overflow-y-auto">
                <!-- Header del Modal -->
                <div class="sticky top-0 bg-white dark:bg-gray-800 border-b border-gray-200 dark:border-gray-700 px-6 py-4 flex items-center justify-between rounded-t-lg">
                    <h2 class="text-xl font-semibold text-gray-800 dark:text-gray-200">
                        Profile
                    </h2>
                    <a 
                        :href="route('dashboard')" 
                        class="text-gray-400 hover:text-gray-600 dark:hover:text-gray-300 transition-colors"
                    >
                        <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"/>
                        </svg>
                    </a>
                </div>

                <!-- Contenido del Modal -->
                <div class="p-6 space-y-6">
                    <div class="bg-gray-50 dark:bg-gray-900 p-6 rounded-lg">
                        <UpdateProfileInformationForm
                            :must-verify-email="mustVerifyEmail"
                            :status="status"
                        />
                    </div>

                    <div class="bg-gray-50 dark:bg-gray-900 p-6 rounded-lg">
                        <UpdatePasswordForm />
                    </div>

                    <div class="bg-gray-50 dark:bg-gray-900 p-6 rounded-lg">
                        <DeleteUserForm />
                    </div>
                </div>
            </div>
        </div>
    </AuthenticatedLayout>
</template>
