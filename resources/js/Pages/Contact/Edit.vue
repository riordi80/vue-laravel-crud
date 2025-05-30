<script setup>
import FileInput from '@/Components/FileInput.vue';
import InputError from '@/Components/InputError.vue';
import InputLabel from '@/Components/InputLabel.vue';
import PrimaryButton from '@/Components/PrimaryButton.vue';
import TextInput from '@/Components/TextInput.vue';
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { Head, Link, useForm, usePage } from '@inertiajs/vue3';
import { ref } from 'vue';

const page = usePage()

const contact = ref(page.props.contact);

const initialValues = {
    name: contact.value.name,
    phone: contact.value.phone,
    avatar: null,
    privacy: contact.value.privacy,
}

const form = useForm(initialValues);

const onSelectAvatar = (e) => {
    const files = e.target.files;
    if(files.length) {
        form.avatar = files[0]
    }
}

const submit = () => {
    form.post(route('contact.update',contact.value),{
        onSuccess: (e) => {
            contact.value = e.props.contact;
        }
    })
}

</script>

<template>

    <Head title="Editar Contacto" />

    <AuthenticatedLayout>
        <template #header>
            <div class="flex justify-between">
                <h2 class="text-xl font-semibold leading-tight text-gray-800">
                    Editar Contacto
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

                            <Transition
                                enter-active-class="transition ease-in-out"
                                enter-from-class="opacity-0"
                                leave-active-class="transition ease-in-out"
                                leave-to-class="opacity-0"
                            >
                                <p
                                    v-if="form.recentlySuccessful"
                                    class="text-sm text-green-600 text-center"
                                >
                                    Contacto actualizado.
                                </p>
                            </Transition>

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
                                <img class="h-16" :src="`/storage/${contact.avatar}`">
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
                                Actualizar Contacto
                            </PrimaryButton>
                            </div>
                        </form>
                    </div>
                </div>
            </div>
        </div>
    </AuthenticatedLayout>
</template>
