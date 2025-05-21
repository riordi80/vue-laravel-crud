<script setup>
import FileInput from '@/Components/FileInput.vue';
import InputError from '@/Components/InputError.vue';
import InputLabel from '@/Components/InputLabel.vue';
import PrimaryButton from '@/Components/PrimaryButton.vue';
import TextInput from '@/Components/TextInput.vue';
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { Head, Link, useForm } from '@inertiajs/vue3';

const initialValues = {
    name: "",
    phone: "",
    avatar: null,
    privacy: "private",
}

const form = useForm(initialValues);

const onSelectAvatar = (e) => {
    const files = e.target.files;
    if(files.length) {
        form.avatar = files[0]
    }
}

const submit = () => {
    form.post(route('contact.store'))
}

</script>

<template>

    <Head title="Crear Contacto" />

    <AuthenticatedLayout>
        <template #header>
            <div class="flex justify-between">
                <h2 class="text-xl font-semibold leading-tight text-gray-800">
                    Crear Contacto
                </h2>
                <Link :href="route('contact.index')">
                Lista de Contactos</Link>
            </div>
        </template>

        <div class="py-12">
            <div class="mx-auto max-w-7xl sm:px-6 lg:px-8">
                <div class="overflow-hidden bg-white shadow-sm sm:rounded-lg">
                    <div class=" flex justify-center p-6 text-gray-900">
                        <form class="w-1/3 py-5 space-y-3" @submit.prevent="submit">
                            <div>
                                <InputLabel for="name" value="Nombre" />

                                <TextInput
                                    id="name"
                                    type="text"
                                    class="mt-1 block w-full"
                                    v-model="form.name"
                                    autofocus
                                    autocomplete="name"
                                    placeholder="Nombre"
                                />

                                <InputError class="mt-2" :message="form.errors.name" />

                            </div>
                            <div>
                                <InputLabel for="phone" value="Telefono" />

                                <TextInput
                                    id="phone"
                                    type="text"
                                    class="mt-1 block w-full"
                                    v-model="form.phone"
                                    placeholder="+34 928 000 000"
                                />

                                <InputError class="mt-2" :message="form.errors.phone" />

                            </div>
                            <div>
                                <InputLabel for="avatar" value="Avatar" />

                                <FileInput
                                    name="avatar"
                                    @change="onSelectAvatar"
                                />

                                <InputError class="mt-2" :message="form.errors.avatar" />

                            </div>
                            <div>
                                <InputLabel for="privacy" value="Visibilidad" />

                                <select v-model="form.privacy" name="privacy" id="privacy"
                                class="w-full mt-1 rounded-md border-gray-300 shadow-sm focus:border-indigo-500 focus:ring-indigo-500">
                                    <option value="private">Privado</option>
                                    <option value="public">Público</option>
                                </select>

                                <InputError class="mt-2" :message="form.errors.privacy" />

                            </div>
                            <div class="flex justify-center pt-3">
                            <PrimaryButton>
                                Crear Contacto
                            </PrimaryButton>
                            </div>
                        </form>
                    </div>
                </div>
            </div>
        </div>
    </AuthenticatedLayout>
</template>
