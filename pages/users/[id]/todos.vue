<template>
    <div class="h-100 w-100">
        <div class="w-100 py-2 d-flex align-center flex-gap-10" @click="routerBack">
            <v-icon icon="mdi-arrow-left"></v-icon>
            <p class="text-h6">Back</p>
        </div>
        <div class="w-100 h-100 d-flex flex-column px-8 overflow-y-auto flex-gap-10">
            <v-card v-for="todos in data.todos" :key="todos.id">
                <v-card-title class="font-weight-bold">{{ todos.todo }}</v-card-title>
                <div class="d-flex flex-gap-10 px-4">
                    <p>Status: </p>
                    <v-icon :icon="todos.completed ? 'mdi-check-circle' : 'mdi-close-circle'" :class="todos.completed ? 'text-green' : 'text-red'"></v-icon>
                </div>
            </v-card>
        </div>
    </div>
</template>

<script setup>

const router = useRouter()
const routerBack = () => {
    router.back()
}
const { id } = useRoute().params
const { data } = useFetch(`https://dummyjson.com/users/${id}/todos`)
</script>

<style>
.flex-gap-10 {
    gap: 10px;
}
</style>