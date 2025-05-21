<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { Head, Link, usePage } from '@inertiajs/vue3';
import { ref } from 'vue';

const props = defineProps({
  contacts: Array
})
</script>

<template>

    <Head title="Contactos" />

    <AuthenticatedLayout>
        <template #header>
            <div class="flex justify-between">
                <h2 class="text-xl font-semibold leading-tight text-gray-800">
                    Contactos
                </h2>
                <Link :href="route('contact.create')">
                Crear Contacto</Link>
            </div>
        </template>

        <div class="py-12">
            <div class="mx-auto max-w-7xl sm:px-6 lg:px-8">
                <div class="overflow-hidden bg-white shadow-sm sm:rounded-lg">

                    <div class="relative overflow-x-auto">
                        <table class="w-full text-sm text-left rtl:text-right text-gray-500 dark:text-gray-400">
                            <thead class="text-xs text-gray-700 uppercase bg-gray-50 dark:bg-gray-700 dark:text-gray-400">
                                <tr>
                                    <th scope="col" class="px-6 py-3">
                                        Nombre
                                    </th>
                                    <th scope="col" class="px-6 py-3">
                                        Teléfono
                                    </th>
                                    <th scope="col" class="px-6 py-3">
                                        Visibilidad
                                    </th>
                                    <th scope="col" class="px-6 py-3">
                                        Avatar
                                    </th>
                                    <th scope="col" class="px-6 py-3">
                                        Acciones
                                    </th>
                                </tr>
                            </thead>
                            <tbody>
                                <tr v-for="contact in props.contacts" :key="contact.id" class="bg-white border-b dark:bg-gray-800 - dark:border-gray-50">
                                    <th scope="row" class="px-6 py-4 font-medium text-gray-900 whitespace-nowrap dark:border-gray-50">
                                        {{ contact.name }}
                                    </th>
                                    <td class="px-6 py-4">
                                        {{ contact.phone }}
                                    </td>
                                    <td class="px-6 py-4">
                                        {{ contact.privacy }}
                                    </td>
                                    <td class="px-6 py-4">
                                        <img class="h-10" :src="`/storage/${contact.avatar}`">
                                    </td>
                                    <td class="px-6 py-4">
                                        <div class="space-x-4">
                                            <Link :href="route('contact.edit', contact)">
                                            Editar
                                            </Link>
                                            <Link :href="route('contact.destroy', contact)" method="delete" as="button">
                                            Eliminar
                                            </Link>
                                        </div>
                                    </td>
                                </tr>
                            </tbody>
                        </table>

                    </div>








                </div>
            </div>
        </div>
    </AuthenticatedLayout>
</template>
