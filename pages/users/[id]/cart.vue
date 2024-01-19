<template>
    <div class="h-100 w-100">
        <div class="w-100 py-2 d-flex align-center flex-gap-10" @click="routerBack">
            <v-icon icon="mdi-arrow-left"></v-icon>
            <p class="text-h6">Back</p>
        </div>
        <div class="w-100 h-100 d-flex flex-column px-8 overflow-y-auto flex-gap-10">
            {{ data }}
        </div>
    </div>
</template>


<script setup>

const router = useRouter()
const routerBack = () => {
    router.back()
}
const { id } = useRoute().params
const { data } = useFetch(`https://dummyjson.com/users/${id}/carts`)

</script>

<style>
.flex-gap-10 {
    gap: 10px;
}
</style>